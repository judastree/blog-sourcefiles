title: "LeetCode: Merge Sorted Array"
date: 2015-08-07 08:54:00
tags: [算法,LeetCode]
---

##题目

[Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

把两个有序的数组合并成一个，数组1有m个元素，数组2有n个元素。假设数组1有足够的长度（m+n）来容纳数组1和数组2，求合并后的数组1.

##思路

因为不能用额外的存储空间，考虑用类似选择排序的方式来重新生成nums1.

即，原nums1的最大值和num2的最大值比较，大者放到新nums1[m+n-1]位置。
并且指针向前移一位，继续比较原nums1和num2的最大值，把大的放到新nums1[m+n-2]位置，直到一个数组的指针已经到头了。


##实现

JavaScript:

        /**
         * @param {number[]} nums1
         * @param {number} m
         * @param {number[]} nums2
         * @param {number} n
         * @return {void} Do not return anything, modify nums1 in-place instead.
         */
        var merge = function(nums1, m, nums2, n) {
        
            var k = 0,i= 0,j=0;
        
            if(m===0&&n===0){
                nums1.length = 0;
                return nums1;
            }
            if(n===0){
                nums1.length = m;
                return nums1;
            }
            if(m===0){
                for(;i<n;i++){
                    nums1[i] = nums2[i];
                }
                nums1.length=n;
                return nums1;
            }
            //i指向原nums1中最大的数，j指向nums2中最大的数
            while(i<m&&j<n){
                //把较大的数放在nums1[m+n-1-k]中
                if(nums1[m-1-i]>=nums2[n-1-j]){
                    nums1[m+n-1-k]  = nums1[m-1-i];
                    i++;
                }else{
                    nums1[m+n-1-k]  = nums2[n-1-j];
                    j++;
                }
                k++;
            }
            if(i===m){
                while(j<n){
                    nums1[m+n-1-k] = nums2[n-1-j];
                    j++;
                    k++;
                }
            }
        };


##耗时

 ![mergesortedarray](/images/mergesortedarray.png)
 