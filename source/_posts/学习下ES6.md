title: "学习下ES6"
date: 2015-07-15 11:26:29
tags: [JavaScript]
---

主要是看阮一峰的[入门教程](http://es6.ruanyifeng.com/#docs/intro)
还有csdn上的[探秘ES6](http://www.csdn.net/tag/%E6%8E%A2%E7%A7%98es6/news)
github上的[es6 feature](https://github.com/lukehoban/es6features)

说起来好惭愧，一直都没有去了解ECMAScript,枉做前端。

ES6有哪些酷炫的新特性呢？

## 新增箭头操作符=> ,简化函数书写
 coffeescript的语法糖里也是有样，各种回调需要写function,现在用=> 代替function关键字

## 新增基本类型 
 JS有null,undefined,boolean,number,string五种基本类型，object是引用类型。
 现在新增Symbol这个基本类型，避免与已有代码命名冲突
 
    var key = Symbol("key");
 
## 自带Promise
 现在已经很多js的类库都支持Promise了，比如Jquery。ES6正式引入，提供原生的Promise对象。
 
##新增块级变量的定义 关键字let
 JS是变量var定义是不存在块级生命周期的。现在新增let关键字，仅可以在块级中使用。
 
     for(let i = 0; i < arr.length; i++){}
     
     console.log(i)
     //ReferenceError: i is not defined
 
##变量的解构赋值
 自动解析数组或对象中的值，并给对应变量进行赋值，这被称为解构（Destructuring）。
 
     
     var [x,y]=getVal(),//函数返回值的解构
         [name,,age]=['wayou','male','secrect'];//数组解构
     
     function getVal() {
         return [ 1, 2 ];
     }
     
     console.log('x:'+x+', y:'+y);//输出：x:1, y:2 
     console.log('name:'+name+', age:'+age);//输出： name:wayou, age:secrect
 
 据说在函数传参中很有用。
 如果函数的参数列表很长，又不想记住他们的顺序，我们对参数对象使用解构赋值，这样，在访问对象属性时，便可以避免重复调用这一参数对象    

##for of 的遍历
   我们以前用for in 遍历数组，但拿到的是数组的索引值，这点很烦。for of 拿到的值不是索引，完全没有这个烦恼。
   
       for (var value of myArray) { 
           console.log(value); 
       }
   
   另外，我们以前也用forEach遍历数组，for(var i of array){} 和forEach(function(i){})比起来，优势在于还可以有break,continue,return这些操作。
   
##Generator函数

  没有看明白这是干什么，mark下
  
##引入模块化 Module
  模块功能主要由两个命令构成：export和import。
  export命令用于用户自定义模块，规定对外接口；
  import命令用于输入其他模块提供的功能，同时创造命名空间（namespace），防止函数名冲突。
  这个对于代码管理很有用啊。越来越像java了...
  
##还有一些其他的新增api，新增的map和set集合等等，到时再看了。