title: "LeetCode:Single Number"
date: 2015-07-22 10:58:33
tags: [算法,LeetCode]
---

##题目来源

[找出落单的数字](https://leetcode.com/problems/single-number/)

有一个都是整型的数组，它除了一个元素只有出现一次之外，其他的都出现了二次。求这个落单的数字。

比如[1,2,3,5,2,1,3]这个数组中5是落单的数字，其他数字都出现了两次。


##思路

最先写的是两层for循环来比较是否有相等的。但是提交之后发现Time Limit Exceeded，时间复杂度是n^2。

题目有标注是线性的事件复杂度，而且空间复杂度也是线性级别的,所以递归调用也是不行的。

然后百度了下，发现有人用异或操作来判断。

    a ^ b = b ^ a
    a ^ a = 0
    0 ^ a = a
    
    a ^ b ^ a = a ^ a ^ b = 0 ^ b = b
    
    
 这样就可以把这个b找出来了。
   
##实现

JavaScript:

       /**
        * @param {number[]} nums
        * @return {number}
        */
       var singleNumber = function(nums) {
           var result = nums[0];
       
           for(var i = 1; i < nums.length; i++){
               result = result ^ nums[i];
           }
           return result;
           
       }
       
 
 ![SingleNumberRuntime](/images/singlenumber.png)      
    

