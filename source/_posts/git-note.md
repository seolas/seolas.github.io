---
title: Git 笔记
date: 2023-12-21 22:54:09
tags: [git]
---

[参考教程](https://www.liaoxuefeng.com/wiki/896043488029600)

[官方文档](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%85%B3%E4%BA%8E%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6)

# 命令

## git config

配置用户

```bash
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```
- `--system` 每个用户的配置
- `--global` 针对当前用户, 生成的文件在 `用户主目录/.gitconfig`
- 不带选项, 针对该仓库, 生成 `.git/config` 文件

查看所有配置

```bash
git config --list --show-origin
```

命令太长了记不住? 用别名

```bash
git config --global alias.lg "log --graph --pretty=oneline --abbrev-commit"
# 以后就是可以直接用
git lg
```

该配置文件的内容

```bash
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[user]
    email = maifeng868@gmail.com
    name = Dreamcats
[remote "origin"]
    url = git@github.com:michaelliao/learngit.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[alias]
    last = log -1
```

## .gitignore

[github 准备好了各种 gitignore 文件](https://github.com/github/gitignore)


`*` 匹配 0 个或多个字符, 排除所有 .class 文件:

```
*.class
```

`**` 匹配任意中间目录, 忽略 doc/ 目录及其子目录下的 .pdf 文件

```
doc/**/*.pdf
```

不排除 .gitignore

```
!.gitignore
```

`/` 开头防止递归, 只忽略当前目录下的 TODO 文件, 不忽略 subdir/TODO

```
/TODO
```

`/` 结尾指定目录, 忽略任何目录下的 build 文件夹

```
build/
```

强制添加被忽视的文件

```bash
git add -f App.class
```

检查是哪个规则忽视了文件

```bash
git check-ignore -v App.class
```

## git init

初始化仓库

```bash
git init
```

## git add

跟踪新文件 / 将修改添加到暂存区

```bash
git add readme.txt
```

## git status

查看文件状态

```bash
git status
```

## git commit

将暂存区内容提交到分支

```bash
git commit -m "wrote a readme file"
```

把所有已跟踪的文件暂存起来一起提交

```bash
git commit -a -m "wrote a readme file"
```

如果提交完了, 发了漏掉了几个文件没有添加, 或者提交信息写错了, 想要重新提交

```bash
git commit --amend
```

## git diff

[比较工作区和暂存区的差异](https://blog.csdn.net/weixin_36750623/article/details/96308336)

```bash
git diff readme.txt 
```

比较已暂存和最后一次提交的差异

```bash
git diff --cached
```

比较工作区和分支的修改

```bash
git diff HEAD -- readme.txt 
```

## git rm

[删除工作区的文件, 并将修改添加到暂存区](https://blog.csdn.net/qq_39505245/article/details/119857986)

```bash
git rm test.txt
```

> 如果暂存区已有该文件的未提交的修改, 需使用 `-f` 选项

从暂存区中移除文件, 但在工作区保留

```bash
git rm --cached test.txt
```

## git mv

重命名文件

```bash
git mv source.txt dest.txt
```

## git reset

撤销暂存区的修改, 放回工作区

```bash
git reset HEAD readme.txt
```

退回到上一次提交

```bash
git reset --hard HEAD^
git reset --hard HEAD~1
git reset --hard 1094adb
```

> HEAD 表示当前版本, 上一个版本就是 HEAD^, 上上一个版本就是 HEAD^^, 写 100 个 ^ 比较容易数不过来, 所以写成 HEAD~100

## git checkout

丢弃工作区的修改

```bash
git checkout -- readme.txt
```

切换到 dev 分支

```bash
git checkout dev
```

创建并切换到 dev 分支

```bash
git checkout -b dev
```

clone 后, 只能看到 master 分支, 要拉取其他分支到本地

```bash
git checkout -b dev origin/dev
```

## git log

查看提交日志

```bash
git log
git log --pretty=oneline
# 查看分支合并情况
git log --graph --pretty=oneline --abbrev-commit
```

## git reflog

查看提交日志, 包括退回的

```bash
git reflog
```

## git clone

克隆远程到本地

```bash
git clone git@github.com:michaelliao/gitskills.git
```

## git remote

查看远程仓库

```bash
git remote -v
```

查看某个远程仓库

```bash
git remote show origin
```

关联远程仓库

```bash
git remote add origin git@github.com:michaelliao/learngit.git
```

修改远程仓库的引用名

```bash
git remote rename orign orign2
```

解除本地和远程的绑定关系

```bash
git remote rm origin
```

## git fetch

拉取远程, 不合并

```bash
git fetch orign
```

## git pull

拉取远程, 合并

```bash
git pull
```

## git rebase

把本地分叉的历史整理成一条直线

```bash
git rebase
```

## git push

推送到远程仓库

```bash
git push origin master
```

>第一次推送时, 要关联本地分支和远程分支, 使用 `-u`

推送标签到远程

```bash
git push origin v1.0
# 推送所有
git push origin --tags
```

删除远程标签

```bash
git push origin :refs/tags/v0.9
```

## git branch

创建分支

```bash
git branch dev
```

查看当前分支

```bash
git branch
```

删除分支

```bash
git branch -d dev
# 删除未合并的分支
git branch -D feature-vulcan
```

本地新建了 dev 分支, 要关联本地和远程 的 dev 分支

```bash
git branch --set-upstream-to=origin/dev dev
```

## git switch

创建并切换到 dev 分支

```bash
git switch -c dev
```

切换到 dev 分支

```bash
git switch dev
```

## git merge

把 dev 分支的内容合并到 master

```bash
git checkout master
git merge dev
# 保留分支名称
git merge --no-ff -m "merge with no-ff" dev
```

> 出现冲突时, 修改文件解决冲突后, 再 add commit

## git stash

将工作区修改 stash

```bash
git stash
```

查看 stash

```bash
git stash list
```

恢复 stash, 但 stash 不删除

```bash
git stash apply
# 恢复指定的 stash
git stash apply stash@{0}
```

删除 stash

```bash
git stash drop
```

恢复的同时把stash内容也删了

```bash
git stash pop
```

## git cherry-pick

把 4c805e2 这个提交所做的修改复制到dev分支, 会自动提交

```bash
git checkout dev
git cherry-pick 4c805e2
```

## git tag

打标签

```bash
# 默认标签是打在最新提交的commit上的
git tag v1.0
git tag v0.9 f52c633
# 创建带说明的标签
git tag -a v0.1 -m "version 0.1 released" 1094adb
```

列出标签

```bash
git tag
```

查看标签信息

```bash
git show v0.9
```

删除标签

```bash
git tag -d v0.1
```

删除本地标签

```bash
git tag -d v0.9
```

## ssh

创建 SSH Key

```bash
ssh-keygen -t rsa -C "youremail@example.com"
```

```bash
ssh -T git@github.com
```

# 使用场景

## 修改提交人

```bash
# 如果不需要修改提交信息, 使用 --no-edit
git commit --amend --author="seolas<contact@seolas.fun>"
```