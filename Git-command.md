# 基本命令

教程：[阮一峰Git教程](https://www.bookstack.cn/read/git-tutorial/README.md)

## 创建仓库

添加空白仓库

```shell
git init
git init NewDir
```

将文件添加到存储库

```sh
git add <file name>
```

克隆仓库

```shell
git clone https://github.com/onmpw/marked.git
```

克隆分支

```shell
git clone -branch master https://github.com/onmpw/marked.git 
```

克隆标签

```shell
git clone -b v1.0 https://github.com/onmpw/marked.git 
```

查看远程仓库

```shell
git remote -v
```

添加远程仓库

```shell
git remote add origin https://gitee.com/lianbing/MapDemo.git
```

拉取仓库

```shell
git fetch <remote_url>
```

拉取并合并(pull=fetch+merge)

```shell
git pull origin master
```

查看远程仓库

```shell
git remote show origin
```

删除远程仓库

```shell
git push origin --delete <branch_name>
```

修改远程仓库地址

```
git remote set-url origin https://gitee.com/jfdfsdd/MapDemo.git
```

## 分支合并

`git branch`命令可以列出本地的所有分支。

```
$ git branch
```

创建一个名为`MyBranch`的新分支，但是依然停留在当前分支。

```
$ git branch MyBranch
```

在远程主机`origin`上创建一个`MyBranch`的分支，并与本地的同名分支建立追踪关系。

```
$ git push -u origin MyBranch
```

将当前分支改名为`MyBranch`。

```
$ git branch -m MyBranch
```

删除`MyBranch`分支，前提是该分支没有未合并的变动。

```
$ git branch -d MyBranch
```

强制删除`MyBranch`分支，不管有没有未合并变化。

```
$ git branch -D MyBranch
```

切换到`MyBranch`分支，当前的工作区会变为`MyBranch`分支的内容。

```
$ git checkout MyBranch
```

基于`MyBranch`分支创建一个新的`NewBranch`分支，新的`NewBranch`分支将成为当前的工作区。

```
$ git checkout -b NewBranch MyBranch
```

## 标签命令

> 标签代表历史版本，当发布不同的版本就使用标签

创建标签

```shell
git tag v1.0
```

标签列表

```shell
git tag
```

查看标签的具体修改信息

```shell
git show v1.0
```

创建附注标签

```
git tag -a v1.4 -m "my version 1.4"
```

推送到远程

```
git push origin v1.5
```

删除本地标签

```
git tag -d v1.0
```



## 文件暂存

> 场景：暂时保存没有提交的工作，所有没有commit的代码，都会暂时从工作区移除，回到上次commit时的状态

基本命令

```shell
# 暂时保存没有提交的工作
$ git stash

# 恢复最近一次stash的文件
$ git stash pop

# 丢弃最近一次stash的文件
$ git stash drop

# 删除所有的stash
$ git stash clear
```

查看内部保存多次修改

```shell
$ git stash list
stash@{0}: WIP on new-feature: 5cedccc Try something crazy
stash@{1}: WIP on new-feature: 9f44b34 Take a different direction
stash@{2}: WIP on new-feature: 5acd291 Begin new feature
```

上面命令假设曾经运行过`git stash`命令三次。

`git stash pop`命令总是取出最近一次的修改，但是可以用`git stash apply`指定取出某一次的修改。

```shell
$ git stash apply stash@{1}
```

上面命令不会自动删除取出的修改，需要手动删除。

```shell
$ git stash drop stash@{1}
```

## 提交历史

主要用于查看 Git 的提交历史

`git log`命令按照提交时间从最晚到最早的顺序，列出所有 commit。

```shell
# 列出当前分支的版本历史
$ git log

# 查看所有分支的操作记录
$ git reflog

# 列出某个文件的版本历史，包括文件改名
$ git log --follow [file]
```

查看最近分支信息

```shell
# 查看每行分支记录
$ git log --oneline

# 查看最近(2次)提交信息
$ git log -2

# 显⽰2周前开始到现在的历史记录,(since 2周前到现在 before 显示截至到2周前)
$ git log --since="2 weeks ago"
```

查看远程分支的变动情况。

```shell
$ git log remote/branch
```

查找log，搜索commit信息，`-i`表示搜索时忽略大小写。

```shell
$ git log --author=Andy$ git log -i --grep="Something in the message"
```

查看某个范围内的commit

```shell
$ git log origin/master..new
```

美化输出

```shell
git log --graph --decorate --pretty=oneline --abbrev-commit
```
