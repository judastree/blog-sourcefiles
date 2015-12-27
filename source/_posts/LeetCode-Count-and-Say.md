title: "LeetCode:Count and Say"
date: 2015-08-06 10:53:41
tags: [算法, LeetCode]
---

##题目

[Count And Say](https://leetcode.com/problems/count-and-say/)

The count-and-say sequence is the sequence of integers beginning as follows:
1, 11, 21, 1211, 111221, ...

1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2, then one 1" or 1211.
Given an integer n, generate the nth sequence.

Note: The sequence of integers will be represented as a string.

##思路
递归的实现，找出CountAndSay(n)和CountAndSay(n-1)的关系。
比如1211拿一个数组记录下有多少个数组。

##实现

JavaScript:

        /**
         * @param {number} n
         * @return {string}
         */
        var countAndSay = function(n) {
            if(n===0) return "";
            if(n===1) return "1";
            if(n===2) return "11";
        
            var preStrArray = countAndSay(n-1).split("");
            var tempArray=[];
        
            tempArray[0] = 1;
            tempArray[1] = preStrArray[0];
            for(var i = 1; i<preStrArray.length-1;i++){
                if(preStrArray[i]!==preStrArray[i-1]){
                    tempArray.push(1);
                    tempArray.push(preStrArray[i]);
                }else{
                    tempArray[tempArray.length-2]++;
                }
            }
            if(preStrArray[i]!==preStrArray[i-1]){
                tempArray.push(1);
                tempArray.push(preStrArray[i]);
            }else{
                tempArray[tempArray.length-2] ++;
            }
            return tempArray.toString().replace(/,/g,"");
        }

##耗时

![countandsay.png](/images/countandsay.png)