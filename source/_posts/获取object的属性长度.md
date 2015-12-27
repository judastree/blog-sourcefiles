title: "计算Object的长度"
date: 2015-07-27 19:22:11
tags: [JavaScript]
---

##题目

对于Object来说，其实没有长度的概念，所以也并没有length的属性或者size()的方法来获取。

那如果想要计算这个object中定义了多少属性值呢？(从Ojbect继承过来的不算)


##思路

方法1:  Object中有hasOwnProperty()的方法，可以判断对象是否有某个特定的属性。
for-in 可以查找object的所有属性。而hasOwnProperty是判断本身对象的属性，不查找原型链的属性，这正好是我们要的。

方法2:  Object还有另外一个keys的方法，可以返回所有的keys。

##实现

方法1:
    
        var obj = {a:"1",b:"2",c:"3"},length=0;
        
        for (var property in obj) {
            if (obj.hasOwnProperty(property)) {
                length++;
            }
        }
    
       console.log(length);
       
       
方法2:

       var obj = {a:"1",b:"2",c:"3"};       
       console.log(Object.keys(obj).length);
    



