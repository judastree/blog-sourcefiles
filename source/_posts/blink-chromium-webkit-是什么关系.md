title: "blink chromium webkit 是什么关系"
date: 2015-07-19 22:06:01
tags: [工具]
---

转帖：[原文](http://blog.csdn.net/milado_nju/article/details/8805810)

Google退出WebKit项目，创建自己的渲染引擎Blink。这其实不能说完全没有先兆，合合分分，纯属正常。

其实，之前关于WebKit2，双方的争论就非常的大。Apple希望它可以随便加入和删除代码而无需担心它会破坏其它Ports的代码，这遭到很多人的反对和不满。

同时，另一方面，Google有很多新的功能希望加入WebKit中，但是WebKit可能并不认可他们。双方分歧越来越多，终于分道扬镳。

这里面有个误区，就是Google的Blink是一个全新的引擎。其实不是这样，Blink目前就是从WebKit直接复制出一个版本出来，然后将与chromium无关的Ports全部移除掉，将代码结构重新整理，就目前而言，Blink的渲染和WebKit是一样，但是，以后两者将各自走不同的路。这有点类似于之前WebKit从KHTML中复制出来一样，历史总是惊人的相似。

目前参与Blink和Chromium大致一样，拥有Chromium的commit权限对Blink也适用。原来一些WebKit的committer和reviewer也开始成为blink的committer。它的提交代码流程，review流程等都是chromium的风格，这对chromium的开发者来说非常熟悉。

