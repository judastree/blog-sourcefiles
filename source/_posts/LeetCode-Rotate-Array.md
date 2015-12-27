title: "LeetCode:Rotate Array "
date: 2015-07-23 11:12:43
tags: [算法,LeetCode]
---

##题目来源
 [数组向右移K位](https://leetcode.com/problems/rotate-array/)
 
 有一个数组[1,2,3,4,5],向右移k位，k=3输出[3,4,5,1,2],k=1输出[5,1,2,3,4]
 
 要求时间复杂度线性，空间复杂度可控O(1)
 
##思路

找到每个元素移位后的位置，在新的数组上追一赋值。

##实现

JavaScript:

        /**
         * @param {number[]} nums
         * @param {number} k
         * @return {void} Do not return anything, modify nums in-place instead.
         */
        var rotate = function(nums, k) {
              //步数是长度的倍数则直接返回
              if(k%nums.length===0){
                return;
            }else{
                //取模，拿到真正的步数，因为k可能大于length
                var step = k%nums.length;
                var result = [];
                result.length =nums.length;
        
                for(var i=0;i<nums.length;i++){
                    //确定每个元素的新的位置
                    result[(i+step)%nums.length] = nums[i]
                }
                //重新赋值
                for( i=0;i<nums.length;i++){
                    nums[i] = result[i];
                }
        
            }
        };


PS：验证虽然通过了，但总感觉有点投机，因为我重新复制了一下这个数组。虽然只用了这一个额外变量，但从空间存储上还是O(n)的。

![RotateArray](/images/rotatearray.png)