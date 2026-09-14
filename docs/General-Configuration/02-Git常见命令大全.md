# Git 常见命令大全
> Git 操作作为大模型项目开发、代码管理、版本迭代和团队协作中的基础能力，主要用于记录代码修改、管理不同版本、创建分支、合并代码、回滚错误以及同步远程仓库。熟练掌握 Git 常见命令，可以让开发过程更加安全、高效、可追踪。

## Git 仓库配置

```bash
# 在当前目录新建一个Git代码库
git init

# 下载一个仓库和它的整个代码历史
git clone 仓库地址

# 下载一个仓库的具体分支
git clone -b 分支名称 仓库地址
```

## Git 基础配置

```bash
# 显示当前的Git配置
git config --list

# 设置提交代码时的用户信息
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
```

## Git 增加/删除文件

```bash
# 添加指定文件到暂存区
git add 文件or文件夹 ...

# 添加当前目录的所有文件到暂存区
git add .

# 删除工作区文件，并且将这次删除放入暂存区
git rm 文件or文件夹...

# 停止追踪指定文件，但该文件会保留在工作区
git rm --cached 文件or文件夹
```

## Git 代码提交

```bash
# 提交暂存区到仓库区
git commit -m "你的提交说明"

# 提交暂存区的指定文件到仓库区
git commit 文件or文件夹 ... -m "你的提交说明"

# 提交工作区自上次commit之后的变化，直接到仓库区
git commit -a

# 提交时显示所有diff信息
git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
git commit --amend -m "你的提交说明"

# 重做上一次commit，并包括指定文件的新变化
git commit --amend 文件or文件夹 ...
```

## Git 分支操作

```bash
# 列出所有本地分支
git branch

# 列出所有远程分支
git branch -r

# 列出所有本地分支和远程分支
git branch -a

# 新建一个分支，但依然停留在当前分支
git branch 分支名

# 新建一个分支，并切换到该分支（旧版Git写法）
git checkout -b 新分支名

# 切换到指定分支，并更新工作区（旧版Git写法）
git checkout 分支名

# 切换到上一个分支（旧版Git写法）
git checkout -

# 新建一个分支，并切换到该分支（新版Git写法）
git switch -c 新分支名

# 切换到指定分支，并更新工作区（新版Git写法）
git switch 分支名

# 切换到上一个分支（新版Git写法）
git switch -

# 合并指定分支到当前分支
git merge 分支名

# 删除远程分支
git push origin --delete 分支名
git branch -dr 分支名
```

## Git 标签管理

```bash
# 列出所有tag
git tag

# 新建一个tag在当前commit
git tag 标签名

# 新建一个tag在指定commit
git tag 标签名 "你的提交说明"

# 删除本地tag
git tag -d 标签名

# 删除远程tag
git push origin :refs/tags/[tagName]

# 查看tag信息
git show 标签名

# 新建一个分支，指向某个tag
git checkout -b 分支名 标签名
```

## Git 远程仓库管理

```bash
# 下载远程仓库的所有变动
git fetch

# 显示所有远程仓库
git remote -v

# 增加一个新的远程仓库，并命名
git remote add origin 仓库地址

# 将本地main分支推送到远程origin分支，并在本地main与远程main的跟踪关系
git push -u origin main

# 推送代码到远端
git push

# 拉取远端代码
git pull
```

## Git 撤销与回滚管理

```bash
# 恢复暂存区的指定文件到工作区
git restore 文件名

# 重置暂存区的指定文件，与上一次提交ID保持一致，但工作区不变
git restore --staged 文件名

# 重置当前分支的指针为指定提交ID，同时重置暂存区，但工作区不变
git reset --soft HEAD~1

# 重置当前分支的HEAD为指定提交ID，同时重置暂存区和工作区，与指定提交ID一致
git reset --hard HEAD~1

# 新建一个提交ID，用来撤销指定提交ID
# 后者的所有变化都将被前者抵消，并且应用到当前分支
git revert 提交ID
```

## Git 常用组合命令

```bash
git add .
git commit -m "更新内容"
git push
```
