title: "git stash 前缓存当前的修改"
date: 2015-08-20 18:00:29
tags: [工具, git]
---

##场景

本地有修改，暂时不想commit，但又必须git pull 拉去最新的代码。这时可以用git stash来缓存当前的修改。

##步骤

1 先缓存当前修改。
    
    git stash
    
2 拉取最新的代码

    git pull
    
3 拉完最新的之后再恢复之前修改
    
    git stash pop
    
##更多

git stash save "work in progress for foo feature"

当你多次使用 **git stash**命令后，你的栈里将充满了未提交的代码，这时候你会对将哪个版本应用回来有些困惑，

**git stash list**命令可以将当前的Git栈信息打印出来，你只需要将找到对应的版本号，

例如使用 **git stash apply stash@{1}**就可以将你指定版本号为stash@{1}的工作取出来，

当你将所有的栈都应用回来的时候，可以使用 **git stash clear**来将栈清空。
    
##参考
    
  [git stash和git stash pop](http://blog.csdn.net/wh_19910525/article/details/7784901)