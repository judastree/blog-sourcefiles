title: "LeetCode:Power of Two"
date: 2015-07-22 10:30:48
tags: [算法,LeetCode]
---

##题目来源
 [给定一个数判断它是否为2的次方](https://leetcode.com/problems/power-of-two/)
 
 给你一个数字N，求判断它是否是2的次方。比如8是2的3次方，返回true，9不是2的次方，返回false。
 
##思路
  这个题目最初想到的是递归除以2。但考虑到2这个数字比较特殊，它的次方在计算机中的位存储也是很特殊的，所以可以试下位操作。
  
      2 : 10
      4 : 100
      8 : 1000
      16: 10000
      ...
  2的X次方，其二进制是1后面跟X个0；而2的X次方减1的二进制都是1.
      
      1 : 1
      3 : 11
      7 : 111
      15: 1111
      ...
  而2^x 和2^x-1 进行**位与**操作，结果是0.比如8和7
       
         1000
       & 0111
       -------
         0000
  那么我们就可以利用这一点来判断一个数是否为2的次方。     
        

##实现

 JavaScript:
 
        /**
         * @param {number} n
         * @return {boolean}
         */
        var isPowerOfTwo = function(n) {
        
            if(n<=0){return false}
            
            return (n&n-1)===0
        };


![Runtime](/images/poweroftwo.png)