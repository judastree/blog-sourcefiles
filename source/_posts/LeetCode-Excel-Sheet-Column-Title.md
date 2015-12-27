title: "LeetCode:Excel Sheet Column Title"
date: 2015-07-30 10:34:14
tags: [算法,LeetCode]
---

##题目

[Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)

给定一个正数，求它在excel中对应的标头值。

        1 -> A
        2 -> B
        3 -> C
        ...
        26 -> Z
        27 -> AA
        28 -> AB 
        
PS:Excel2003版之前最大是255列，2007版最大是16384列，当然这和题目无关。

##思路

这个题目其实是把十进制的数字转化成26进制。想到之前求一个数的二进制是通过不断除2的方式，这个也一样。

只要除以26之后得到商比26大就拿这商除26，并把每次除法的余数保存起来，直到商为0，将余数们反向输出就是26进制表达了。

##实现

JavaScript:

       /**
        * @param {number} n
        * @return {string}
        */
       var convertToTitle = function(n) {
            var cs=[];
       
           while(n>26){
               if(n%26!==0){
                    //将余数对应的字母插入数组头部
                   cs.unshift(String.fromCharCode(n%26+64));
                   n = Math.floor(n /26);
               }else{
                   //如果刚好整除，那么商减1，余数为26
                   cs.unshift(String.fromCharCode(90));
                   n = Math.floor(n /26) -1;
       
               }
           }
           cs.unshift(String.fromCharCode(n+64));
           return cs.toString().replace(/\,/g,"");
       };
       
  
   ![excelcolumntotile](/images/excelcolumntotitle.png)    
        
        
        