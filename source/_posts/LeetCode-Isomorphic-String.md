title: "LeetCode:Isomorphic Strings"
date: 2015-07-27 10:26:51
tags: [算法, LeetCode]
---

##题目
[Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)

判断两个字符串是否为同型构造的字符串。

比如:

Given "egg", "add", return true.

Given "foo", "bar", return false.

Given "paper", "title", return true.

如果s字符串的字母被替换可以得到t字符串的话，则说明s和t字符串的构造是相同的。

##思路

按照同形构造的定义来，如果字母替换可以得到目标字符串，我们先建一个map来存储s和t/t和s字母的对应关系。
然后分别遍历s和t的字符串，只要出现当前字母和map表的字母不匹配的，就说明s和t不是同源的字母。

##实现

JavaScript:

       /**
        * @param {string} s
        * @param {string} t
        * @return {boolean}
        */
       var isIsomorphic = function(s, t) {
           if(s===t){
               return true;
           }else{
               var sArray= s.split(""),tArray = t.split("");
               var map = {};
       
               for(var i=0;i< sArray.length;i++){
                   //找出t和s 字母的匹配关系
                   if(!map[tArray[i]]){
                       map[tArray[i]] = sArray[i];
                   }else{
                       //如果当前字母和map中取出的字母不匹配，则返回false
                       if(sArray[i]!==map[tArray[i]]){
                           return false;
                       }
                   }
               }
               //清空map，反向查找匹配关系
               map ={};
               for( i=0;i< tArray.length;i++){
                   //找出s和t字母的匹配关系
                   if(!map[sArray[i]]){
                       map[sArray[i]] = tArray[i];
                   }else if(tArray[i]!==map[sArray[i]]){
                       //如果当前字母和map中取出的字母不匹配，则返回false
                       return false;
                   }
       
               }
               return true;
           }
       };
       
##结果
![isomorphicstrings](/images/isomorphicstring.png)


##PS
一开始想的是replace的方法，但是后面验证出来发现输入的字符串有各种需要转义的特殊字符(\*&$')。