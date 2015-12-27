title: "currentColor关键字"
date: 2015-06-30 13:31:24
tags: [css]
---

与其说这是一个css的关键字，但其实说是个变量更好理解一点。

currentColor 代表了当前元素被应用的color颜色值。使用它可以将当前这个颜色值应用到其他属性上，或者嵌套元素的其他属性上。

如果当前元素没有显示地指定一个color值，那么它的颜色值从父级集成而来。


使用了currentColor之后，css更好维护了，一改全改。

	div{
		color: #33; 
		border: 5px solid currentColor;
		box-shadow: 0 0 5px solid currentColor;
	}
	
除了IE8，PC和手机上的浏览器基本都支持这个关键字。
