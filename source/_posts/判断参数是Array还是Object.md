title: "JS判断一个变量是否是Array"
date: 2015-11-04 23:03:39
tags: [JavaScript]
---
##问题描述

用typeof来检查一个变量，不论是array还是object，都将返回‘object'。那么怎样判断一个JavaScript变量是array还是obiect？ 


##方案

 1. 通过该变量的length属性。

    Array类型有length属性，得到是>=0的数值。Object的length是undefined。

    但当该对象自己有length属性时，这个方法失效。

 2. 通过instanceof 方法
 
    a instanceof Array 是一个语法糖，相当于 a.constructor == Array.
    
    这种方法在多个frame的环境下失效，因为每个iframe都有一套自己的执行环境，跨frame实例化的对象彼此是不共享原型链。

 3. Array.isArray()
 
    ECMAScript 5的写法，绝大多数的浏览器支持这种方式，早期的一些浏览器不支持。
    
 4. 用prototype的call方法来实现
 
    这也是Jquery的实现，推荐采用这种。
   
    因为js中每一个function中都会有call方法和prototype属性，并且js在Object.prototype中的tostring函数上做了一个封装，
   
    就是调用toString.call后，会返回[object constructorName]的字符串格式，这里的constructorName就是call参数的函数名
   
 
 
 
 
    Object.prototype.toString.call(arr) == '[object Array]'
   
   
   
   