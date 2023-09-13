# Git 撤退操作

将某次修改撤销到上一个版本，或者想撤销某次多余提交

撤销操作分为以下三种情况

- 未 add 到暂存区
- 已 add 但还没从commit
- 已commit 但还没 push 到远程仓库
- 已 push 到远程仓库



#### 未 add 到暂存区

```
git checkout . //放弃所有修改文件
git restore . //放弃修改所有文件
```

#### 已 add 但未commit

在暂存区(已add操作)保留已修改文件，放弃修改执行工作区操作

```
git reset HEAD fileName //恢复某个文件到工作区
git reset HEAD . 	//恢复所有文件到工作区
git reset 	//恢复所有文件到工作区
```

#### 已commit 但未 push 远程仓库

撤退有以下几种结果：主要由三个选项

结果一、不保存代码修改

```shell
git reset --hard HEAD^ 	//回退上一次commit状态
git reset --hard commit_id 	//回退到某个commit版本、
```

结果二、保存修改

```shell
git reset --mixed HEAD^
git reset HEAD^
```

结果三、只撤销commit 但不撤销add 添加的文件（保存代码修改）

```shell
git reset --soft HEAD^ 
```

结果四、撤销修改并回到最新版本

```shell
git fetch --all
git reset --hard origin/master 
```

 参数详情:

- `reset`：会将暂存区的内容和本地已提交的内容全部恢复到未暂存的状态,不影响原来本地文件(未提交的也不受影响) ,也就是恢复到add之前
- `soft`：不清空暂存区,将已提交的内容恢复到暂存区,不影响原来本地的文件(未提交的也不受影响),也就是恢复到commit之前
- `hard`：清空暂存区,将已提交的内容的版本恢复到本地,本地的文件也将被回退的版本替换，也就是恢复到没开发之前



#### 已 push 到远程仓库

```shell
git reset --hard HEAD^ //回退上一版本
git reset --hard commit_id //回退id版本号位置
git push origin HEAD --force //强制推送到远程，可能会收到保护
```

#### reset 和 revert 的区别

- git revert是用一次新的commit来回滚之前的commit，git reset是直接删除指定的commit
- git reset 是把HEAD向后移动了一下，而git revert是HEAD继续前进，只是新的commit的内容和要revert的内容正好相反，能够抵消要被revert的内容

场景：如果回退分支的代码以后还需要的情况则使用git revert， 如果分支是提错了没用的代码，则使用 git reset
