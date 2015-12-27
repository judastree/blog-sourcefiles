title: "LeetCode:Plus One"
date: 2015-07-22 11:17:26
tags: [算法,LeetCode]
---

##题目来源

[Plus One](https://leetcode.com/problems/plus-one/)

有一个数组代表一个非负的数字，求这个数字+1之后的数组。
比如这个数组是[1,2,3,4]它代表数字1234，那么这个数字加1之后是1235。希望得到这个数字代表的数组[1,2,3,5]

##思路
从最后一位开始，对当前值+1，如果当前值不为9则正常返回结果。如果当前值为9，则当前值变为0，再递归调用前一位的+1操作。


##实现

JavaScript:

       /**
        * @param {number[]} digits
        * @return {number[]}
        */
       var plusOne = function(digits) {
           function plus(digits,i){
               if(digits[i]===9){
                   digits[i]=0;
                   if(i===0){
                       var head = [1];
                       return head.concat(digits);
                   }else{
                       return plus(digits,i-1);
                   }
       
               }else{
                   digits[i] = digits[i]+1;
                   return digits;
               }
       
           }
           return plus(digits,digits.length-1);
       };
      
      
PS：上面的代码性能不是很好，肯定有更好的算法的。
      
 ![PlusOneRuntime](/images/plusone.png)     