title: "Git 部分提交"
date: 2015-08-20 17:39:51
tags: [工具, git]
---

##场景

修改了四个文件，分别涉及到两个功能，需要把其中两个文件的修改当做一个功能的commit，另外两个文件的修改当做另一个功能的commit。

但如果要用git add 的命令，会让当前所有的修改都加入commit。

怎么办呢？

**用git stash 命令**

##步骤

1 用git add 命令添加第一个commit需要的文件
    
        git add file1
    
        git add file2
    
2 隐藏其他修改，git stash 的参数中 -k 开关告诉仓库保持文件的完整  -u 开关告诉仓库包括无路径的文件(那些新的和未添加到git的)
这时git status就只能看到file1 和file2，并且当你切换到实际的文件目录，file3 和file4的修改也随之不见。
   
        git stash -k -u
    
     
3 提交第一个commit
    
        git commit -m 'submit function1'
        
4 恢复之前隐藏的修改,这时再git status，file3和file4的修改又回来。
        
        git stash pop
          
5 提交第二个commit
    
        git commit -m 'submit function2'
        
        
##参考
   [http://www.open-open.com/lib/view/open1413852243809.html](http://www.open-open.com/lib/view/open1413852243809.html)
        
        
        
        


