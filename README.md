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

## 关联链接

[hello-git](https://github.com/linshanzeng/hello-git)

## 参考链接

[Git教程](https://www.liaoxuefeng.com/wiki/896043488029600/898732792973664)
