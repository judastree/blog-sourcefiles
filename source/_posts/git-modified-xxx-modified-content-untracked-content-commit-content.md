title: "git modified:xxx(modified content,untracked content,commit content)"
date: 2015-12-27 21:58:00
tags: [git]
---

git add 或者commit,push的时候发现某个文件夹不能被add,commit,提示当前文件夹 modified:xxx(modified content)

去git远程仓库查看,这个目录是空的.

打开本地仓库的目录,发现xxx目录下有个.git的目录,影响了其父目录的trace.

解决办法:删除.git目录,重新提交
