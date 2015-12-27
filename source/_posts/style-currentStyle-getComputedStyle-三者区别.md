title: "style currentStyle getComputedStyle 三者区别"
date: 2015-07-27 19:58:26
tags: [JavaScript]
---

JS中通过style来获取元素的样式有时并获取不到，为什么呢?

一个元素的样式由三部分组成，嵌入样式，内联样式和外联样式。

   * 内联样式: 写在标签内的样式，<div style=""></div>
   * 嵌入样式: 写在<html>和<head>之间，用<style></style>包住的样式
   * 外联样式: 由<link>标签引入的外部css
   
   
document.getElementById("ID").style 只可以获取到内嵌样式，也就是写在标签内style属性中定义的样式。
  
在IE下可以用**currentStyle**中获取其他样式,但在别的浏览器中不支持。
  
而火狐,chrome等可以通过getComputedStyle这个方法来获取所有计算过的样式。
  
    getComputedStyle(document.getElementById("ID"))
    
    
