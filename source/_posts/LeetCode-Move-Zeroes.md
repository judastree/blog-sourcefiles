title: "LeetCode Move Zeroes"
date: 2015-10-10 20:51:48
tags: [算法,LeetCode]
---

##题目

[Move Zeroes](https://leetcode.com/problems/move-zeroes/)

将一个数组中的0元素都移到最后面，同时保持非0元素的顺序不变。

比如，[0,1,0,3,12] 移动后变成了[1,3,12,0,0]

##思路

  1. 找到第一个0元素的位置，从第一个0元素的位置往后遍历
  2. 发现非0元素，则与第一个0元素互换位置，并将第一个0元素的位置往后移一位。
  3. 继续遍历，重复2动作直到遍历结束。

##实现

Javascript

    /**
     * @param {number[]} nums
     * @return {void} Do not return anything, modify nums in-place instead.
     */
    var moveZeroes = function(nums) {
        var firstzero = 0,temp;
        for(;firstzero<nums.length-1;firstzero++){
            //find first zero
            if(nums[firstzero]===0) break;
        }
        for(var j=firstzero+1;j<nums.length;j++){
            if(nums[j]!==0){
                //non-zero, change and move on
                temp = nums[j];
                nums[j]=nums[firstzero];
                nums[firstzero]=temp;
                firstzero ++;
            }
    
        }
        
    };

##耗时

![movezeroes](/images/movezeroes.png)