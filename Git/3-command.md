#### 回退

1. 回退到上一个会几个版本
- 在git中用 `HEAD` 指向和表示当前版本，上一个版本就是  **HEAD^** ，上上一个版本就是 **HEAD^^** , 上一百个版本 **HEAD~100**。
- git reset --hard HEAD^ 回退到上一个版本

2. 回退到指定的commit
- 用 git log 可以看到git commit 的详细信息，其中一长串的是 commit id，他就是回退的凭证
- 即使用 1 中的命令回退到上一个版本了，如果你知道回退之前的commit id，还是可以利用  git reset --hard commit_id 回到退回之前的版本

#### 重返未来

git reflog 记录每一次命令，查看命令历史

#### 查看差异

- git diff HEAD -- filename 命令查看工作区和版本库里面最新版本的区别

#### 撤销修改

- 撤销 **工作区** 的修改：git checkout -- filename。用版本库里的版本替换工作区的版本
- 撤销 **暂存区（用 git add 已经将改动添加到暂存区）** 的修改：git reset HEAD filename 将修改回到工作区，然后用上面一步的命令将修改丢弃

#### 删除文件

- 在实际的文件夹中删除文件，然后用 git rm filename，将删除的动作提交暂存区

#### 本地文件夹关联远程库

- 关联：git remote add origin git@server-name:path/repo-name.git
- 第一次推送master到远端：git push `-u` origin master

#### 分支操作

- git checkout -b dev：-b参数表示创建并切换
- git merge branchName：合并指定分支到当前分支
  - 禁用Fast forward模式（--no-ff），Git就会在merge时生成一个新的commit
  - git merge `--no-ff` `-m "merge with no-ff"` dev，因为会新生成各个commit，所以用 -m 指定commit 信息

#### 存贮当前工作区文件
- git stash
- git stash list：查看stash的记录。形如：
  - stash@{0}: WIP on dev: f52c633 add merge
- stash内容恢复
  - git stash apply：恢复，但是恢复后，stash内容并不删除。需要用git stash drop来删除
  - git stash pop：恢复的同时把stash内容也删了
- 恢复指定的 stash
  - git stash apply `stash@{0}`

#### 远程仓库

- 远程仓库的默认名称是origin
- `git remote`：查看远程库的信息；用 git remote -v 显示更详细的信息
- git branch --set-upstream-to=origin/<branch> dev：指定本地dev分支与远程origin/dev分支的链接

#### Rebase

- rebase操作可以把本地未push的分叉提交历史整理成直线；
- rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。
