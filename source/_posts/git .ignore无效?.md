title: "git ignore 无效?"
date: 2015-07-14 10:23:49
tags: [git]
---

有一些build文件总是自动生成，为了不想每次提交都更新到仓库里，可以在git的.gitignore文件中设置，忽略这些文件。

但是。

有的时候ignore失效，即使添加了忽略然并卵，为什么呢？

因为在git库中已存在了这些build文件，只要之前push过，这些文件都会加入git的跟踪中。

而.gitignore文件只对还没有加入跟踪的文件起作用。

那么解决办法就很明显了，两个字，删掉！

把原来在仓库里的文件删掉，重新和更新过的.gitignore文件一起提交。

之后ignore文件就生效了。

