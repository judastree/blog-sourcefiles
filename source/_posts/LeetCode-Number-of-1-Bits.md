title: "LeetCode:Number of 1 Bits"
date: 2015-07-26 12:36:48
tags: [算法, LeetCode]
---

##题目

 [找出一个数字的二进制中有多少个1](https://leetcode.com/problems/number-of-1-bits/)
 
 给定一个无符号的整型数字，比如11,它的二进制是1011,所以返回1的个数3.
 
##思路
对二进制进行位操作，每向右移1位和1做位与操作。是1的话计数器加1，直到右移到0截止。

这个方法写得很轻松，但是耗时长。

##实现

JavaScript:

    /**
     * @param {number} n - a positive integer
     * @return {number}
     */
    var hammingWeight = function(n,count) {
        if(!count){
            count = 0;
        }
        if(n&1===1){
            count++;
        }
        if(n>1){
            return hammingWeight(n>>>1,count);
        }else{
            return count;
        }
    };