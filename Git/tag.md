- Git的标签虽然是版本库的快照，但其实它就是指向某个 commit 的指针
- 默认标签是打在最新提交的commit上
- 标签总是和某个commit挂钩。如果这个commit既出现在master分支，又出现在dev分支，那么在这两个分支上都可以看到这个标签


#### 创建标签

- git tag tagName
- 打标签到历史commit：git tag tagName f52c633（commit id）
- 带说明的标签：git tag -a v0.1 -m "version 0.1 released"
  - `-a`：指定标签名
  - `-m`：指定说明文字

#### 查看标签

- 查看所有标签：git tag
  - 标签不是按时间顺序列出，而是按字母排序的
- 查看标签信息：git show tagname

#### 删除标签

- git tag -d tagName：删除本地标签
- 删除远程分支
  - git tag -d tagName：删除本地分支
  - git push origin :refs/tags/tagname：推送到远端

#### 推送标签到远程

- git push origin tagname
- git push origin --tags：一次性推送全部尚未推送到远程的本地标签
