title: "LeetCode:Longest Common Prefix"
date: 2015-08-09 13:52:02
tags: [LeetCode,算法]
---

##题目

   [LeetCode:Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)
   
   找出一个字符串数组中所有元素的最长公共前缀。
   
##思路
   
   先找出这个数组中最短的字符串，然后再遍历数组比较这个最短字符串是否当前元素的前缀。
   如果是的话，比较下一个数组元素。
   如果不是的话，最短字符串截断最后一位再和当前数组数组元素比较，直到最短字符串长度为0.

##实现

JavaScript:


        /**
         * @param {string[]} strs
         * @return {string}
         */
        var longestCommonPrefix = function(strs) {
            if(strs.length===0){
                return "";
            }
            var shortestStr=strs[0];
            //找出最短的字符串
            for(var i =1; i<strs.length;i++){
                if(strs[i].length<shortestStr.length){
                    shortestStr = strs[i]
                }
            }
            //判断最短字符串是否是当前元素的前缀
            for(i=0;i<strs.length;i++){
                while(shortestStr.length>0) {
                    if (strs[i].indexOf(shortestStr) === 0) {
                        break;
                    } else {
                        shortestStr = shortestStr.substring(0,shortestStr.length-1);
                    }
                }
            }
            return shortestStr;
        };
     
        
##耗时   

![Runtime](/images/longestcommonprefix.png)