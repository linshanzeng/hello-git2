# Git教程

## 远程仓库

### 从远程仓库克隆

克隆一个本地库：`git@github.com:linshanzeng/hello-git2.git`

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
切换到main分支：git checkout main
dev分支合并到main分支上：git merge dev
删除dev分支：git branch -d dev
```

### *解决冲突*

查看提交历史以图形：`git log --graph --pretty=oneline --abbrev-commit`

## 关联链接

[hello-git](https://github.com/linshanzeng/hello-git)

## 参考链接

[Git教程](https://www.liaoxuefeng.com/wiki/896043488029600/898732792973664)
