# Git学习笔记

## 远程仓库

### 从远程仓库克隆

克隆一个本地库：`git clone git@github.com:linshanzeng/hello-git2.git`

## 分支管理

创建dev分支：

```text
方法一：
创建dev分支，并切换到dev分支：git checkout -b dev
方法二：
创建dev分支：git branch dev
切换到dev分支：git checkout dev
方法三：
git switch -c dev
方法四：
git branch dev
git switch dev
```

查看分支：`git branch`

dev分支合并到main分支上：

```text
git add readme.txt
git commit -m "branch test"
git switch main
dev分支合并到main分支上：git merge dev
删除dev分支：git branch -d dev
git branch
```

### *解决冲突*

查看提交历史以图形：`git log --graph --pretty=oneline --abbrev-commit`

### *分支管理策略*

```text
git switch -c dev
git add readme.txt
git commit -m "add merge"
git swich master 
强制禁用Fast forward，dev分支合并到main分支上：git merge --no-ff -m "merge with no-ff" dev
```

### *Bug分支*

```text
touch hello.py
git add hello.py
储藏现场：git stash
git switch main
git switch -c issue-101
git add readme.txt
git commit -m "fix bug 101"
git switch main
git merge --no-ff -m "merged fix bug 101" issue-101
git branch -d issue-101
git switch dev
同步修复bug（fix bug 101）：git cherry-pick 2113a85
查看所有现场：git stash list

第一种：
恢复并删除现场：git stash pop
第二种：
恢复现场：git stash apply
删除现场：git stash drop
```

### Feature分支

强制删除：`git branch -D feature-vulcan`

### *多人协作*

查看远程库：git remote
查看远程库详细信息：git remote -v
推送分支：

```text
git push origin main
推送dev分支：git push origin dev
master分支是主分支，推送
dev分支是开发分支，推送
bug分支，可选
feature分支，可选
```

抓取分支

```text
git clone git@github.com:linshanzeng/hello-git2.git
clone后默认只有main分支：git branch
git switch -c dev origin/dev
抓取分支：git pull
指定本地dev分支和远程dev分支链接：git branch --set-upstream-to=origin/dev dev
```

多人协作的工作模式：

```text
1.首先，可以试图用git push origin dev推送自己的修改；
2.如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
3.如果合并有冲突，则解决冲突，并在本地提交；
4.没有冲突或者解决掉冲突后，再用git push origin dev推送就能成功！
如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to=origin/dev dev。
```

Rebase

```text
git push origin main
别人先提交，出现问题：git pull
变基：git rebase
git push origin main

rebase操作可以把本地未push的分叉提交历史整理成直线
```

## 标签管理

### 创建标签

打一个先新标签：`git tag v1.0`

查看所有标签：`git tag`

给某次提交打标签：`git tag v0.9 f52c633`

打一个带说明的标签：`git tag -a v0.1 -m "version 0.1 released" 1094adb`

查看标签信息：`git show v0.9`

### 操作标签

删除一个标签：`git tag -d v0.1`

推送一个标签：`git push origin v1.0`

推送所有未推送的标签：`git push origin --tags`

删除一个远程标签：

```text
git tag -d v0.9
git push origin :refs/tags/v0.9
```

## 使用Gitee

删除已有的GitHub远程库：`git remote rm origin`

关联GitHub远程库：`git remote add github git@github.com:linshanzeng/hello-git2.git`

关联Gitee远程库：`git remote add gitee git@gitee.com:chiyisan/hello-git2.git`

推送到GitHub：`git push github main`

推送到Gitee：`git push gitee master`

## 自定义Git

显示颜色：`git config --global color.ui true`

### 忽略特殊文字

强制添加文件到Git：

```text
方法一：
强制添加：git add -f App.class
方法二：
查看出错规则：git check-ignore -v App.class
修改.gitignore文件
```

### 配置别名

```text
status别名：git config --global alias.st status
checkout别名：git config --global alias.ck checkout
commit别名：git config --global alias.cm commit
branch别名：git config --global alias.br branch
reset HEAD别名：git config --global alias.rs 'reset HEAD'
log -1别名：git config --global alias.last 'log -1'
git log别名：git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
当前仓库配置文件：cat .git/config
当前用户配置文件：cat ~/.gitconfig
```

## 关联链接

[hello-git](https://github.com/linshanzeng/hello-git)

## 参考链接

[Git教程](https://www.liaoxuefeng.com/wiki/896043488029600/898732792973664)

[忽略特殊文件配置文件](https://github.com/github/gitignore)

[Git Cheat Sheet](https://liaoxuefeng.gitee.io/resource.liaoxuefeng.com/git/git-cheat-sheet.pdf)

[Git的官方网站](https://git-scm.com/)
