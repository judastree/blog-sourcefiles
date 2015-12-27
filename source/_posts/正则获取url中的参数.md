title: "正则获取url中的参数"
date: 2015-08-12 22:26:32
tags:  [正则,JavaScript]
---

##思路

url中的参数都是以[&]name=value的形式带在url后面的，而location.search中可以拿到url中？之后的字符串（包括？在内）。

那么通过处理location.search的字符串，即可得到想要的参数。

我们用正则匹配的方式,给一个参数name，求它的value。

    function getQueryString(param){
        var reg = new RegExp('(^|&)' + name + '=([^&]*)(&|$)', 'i');
        var r = window.location.search.substr(1).match(reg);
        if (r != null) {
            return unescape(r[2]);      
        }
        return null;
    }
    
    

这个正则是找以 &name 或者 name 为开头，以 =value& 或者 =value 结尾的字符串，忽略大小写，一次匹配不循环。

以 a=2&b=3&c=4 为例子.

当name=a时:
    
    r= ["a=2&","","2","$"]
 
当name=b时:
    
    r = ["&b=3&","&","3","&"]
    
当name=c时:
    
    r = ["&c=4","&","4",""]
    
##match的用法    

match() 方法将检索字符串 stringObject，以找到一个或多个与 regexp 匹配的文本。

这个方法的行为在很大程度上有赖于 regexp 是否具有标志 g。

如果 regexp 没有标志 g，那么 match() 方法就只能在 stringObject 中执行一次匹配。

如果没有找到任何匹配的文本， match() 将返回 null。否则，它将返回一个数组，其中存放了与它找到的匹配文本有关的信息。

该数组的第 0 个元素存放的是匹配文本，而其余的元素存放的是与正则表达式的子表达式匹配的文本。

除了这些常规的数组元素之外，返回的数组还含有两个对象属性。index 属性声明的是匹配文本的起始字符在 stringObject 中的位置，input 属性声明的是对 stringObject 的引用。

如果 regexp 具有标志 g，则 match() 方法将执行全局检索，找到 stringObject 中的所有匹配子字符串。若没有找到任何匹配的子串，则返回 null。如果找到了一个或多个匹配子串，则返回一个数组。不过全局匹配返回的数组的内容与前者大不相同，它的数组元素中存放的是 stringObject 中所有的匹配子串，而且也没有 index 属性或 input 属性。

注意：在全局检索模式下，match() 即不提供与子表达式匹配的文本的信息，也不声明每个匹配子串的位置。如果您需要这些全局检索的信息，可以使用 RegExp.exec()。    
    
