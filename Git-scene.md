# 常见场景

#### 提交信息错误

如果你的提交信息(commit message)写错了且这次提交还没有推送，通过下面的命令修改提交信息

```shell
git commit --amend --only

git commit --amend --only -m 'xxxxxxx'
```

#### 切换分支的正确使用

> 当开发时，出现紧急Bug 需要修复，但此时功能才开发一半，又不想先 commit 提交，这时就需要代码暂存

第一步：先暂存代码`git stash`

第二步：修改完紧急分支，然后切换到工作分支

第三步：恢复代码 `git stash apply`



#### 如何合并分支

使用`merge`合并，如果有冲突，则会产生分支，难以清理提交记录

`chery-pick`只需要将commit 合并到develop 分支上 ，且不会产生分支，git提交图谱永远保持一条直线，再有，模块分支开发完成后，需要将多个commit 和为一个commit，再合并到develop 分支，避免多个commit，这也是不使用merge的原因

**如何合并staging\release分支**

rebase 译为变基，合并同样不会产生分叉。当 develop 更新了许多功能，要合并到 staging 测试，不可能用 `cherry-pick` 一个一个把 commit 合并过去。因此要通过 `rebase` 一次性合并过去，并且保证了 staging 与 develop 完全同步

#### 查看冲突的来龙去脉

> 在解冲突或者想要知道一段代码的来龙去脉的时候，git blame就是一个很强大的工具

```powershell
git blame <file>
git blame -L start,end <file>
```

查看某个文件之前的修改

```shell
git log --pretty=oneline <file>
git show hash值 <file> 	 #查看修改部分
git show -3 <file>		#之前3次修改
git show hash值:/某个文件  	#查看完整的文件
```

#### 删除最后一次提交

```shell
# 这会不可逆的改变你的历史，搞乱拉取历史
$ git reset HEAD^ --hard  
$ git push -f [remote] [branch]  
```

如果还没有推送到远程，把Git重置(reset)到你最后一次提交前的状态(同时保存暂存的变化):

```shell
(my-branch*)$ git reset --soft HEAD@{1}  
```

==注意==：如果已经推送，唯一安全做法那会创建一个新的提交(commit)用于撤消前一个提交的所有变化(changes)；或者, 如果你推的这个分支是rebase-safe的 (例如：其它开发者不会从这个分支拉), 只需要使用 `git push -f`。

#### 重置后找回内容

> 如果你意外的做了 `git reset --hard`, 你通常能找回你的提交(commit), 因为Git对每件事都会有日志，且都会保存几天

```shell
$ git reflog  
$ git reset --hard SHA1234  
```

#### 暂存内容添加到上一次提交

```shell
$ git commit --amend  
```







https://www.eet-china.com/mp/a249971.html