title: "LeetCode:Valid Anagram"
date: 2015-08-02 12:00:06
tags: [算法,LeetCode]
---
##题目

[Valid Anagram](https://leetcode.com/problems/valid-anagram/)

判断两个字符串是否易位构造，也就是字母种类和出现的次数一样。

比如：

  dear   和  read
  listen 和  silent
  loop   和  pool
  

##思路

统计两个字符串的字母种类和出现的次数，如果相等则是易位构造。


##实现

JavaScript:

       /**
        * @param {string} s
        * @param {string} t
        * @return {boolean}
        */
       var isAnagram = function(s, t) {
           //判断两个字符串是否同源，也就是字母种类和出现的次数一样
           var sArray = s.split(""),tArray= t.split(""),sMap={};
       
           //先判断s和t的长度是否相等
           if(s.length!== t.length){
               return false;
           }
           //获取s字符串的字母种类和每个字母出现的次数
           for(var i=0;i<sArray.length;i++){
               if(!sMap[sArray[i]]){
                   sMap[sArray[i]] = 1;
               }else{
                   sMap[sArray[i]]++;
               }
           }
       
           //根据sMap来判断t字符串是否和s同源
           for(i=0;i<tArray.length;i++){
               if(sMap[tArray[i]]){
                   sMap[tArray[i]]--;
                   if(sMap[tArray[i]]<0){
                       return false;
                   }
               }else{
                   return false;
               }
           }
           return true;
       };
       

PS: 因为这个题目在leetcode上比较新，所以还没有出来JS运行时常的比较。