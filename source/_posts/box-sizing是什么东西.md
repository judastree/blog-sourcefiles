title: "box-sizing 是什么东西"
date: 2015-07-14 09:59:02
tags: [css]
---

昨天有人问我知道盒子模型么？那必须的呀。width,height,margin,padding,border这些的嘛。

然后又问什么是box-sizing?好熟悉，但没概念了。

在说盒子模型的时候，肯定会说IE对盒子模型的支持和其他浏览器不一样。它的width是包含了padding和border的。

CSS3中新增box-sizing属性刚好可以解决这个问题，不用费心去算是否盒子模型不一致了。


    box-sizing: content-box|border-box|inherit;
    
box-sizing的属性值有两种，(inherit继承就不说了)

 + content-box：border 和 padding 不计入width和height （默认的）
 + border-box ：border 和 padding 计入width和height  （IE那种的）