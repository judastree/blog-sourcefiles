title: "LeetCode:Maximum Depth of Binary Tree"
date: 2015-07-23 10:37:29
tags: [算法,LeetCode]
---

##题目来源

[查找二叉树的最大深度](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

##思路
二叉树的最大深度，等于根节点的深度。根节点的深度等于左子树和右子树深度的较大者。

所以这个题可以递归遍历每一个节点的深度。

##实现

JavaScript:

        /**
         * Definition for a binary tree node.
         * function TreeNode(val) {
         *     this.val = val;
         *     this.left = this.right = null;
         * }
         */
        /**
         * @param {TreeNode} root
         * @return {number}
         */
        var maxDepth = function(root) {
            function findDepth(node,currentDepth){
                if(node!==null){
                    currentDepth++;
                    //每个节点的深度，等于左深度和右深度的较大者
                    var leftDepth =  findDepth(node.left,currentDepth);
                    var rightDepth = findDepth(node.right,currentDepth);
                    return leftDepth>rightDepth?leftDepth:rightDepth;
                }else{
                    return currentDepth;
                }
            }
            //返回根节点的深度
            return findDepth(root,0);
        };
        
        
![MaxDepth](/images/maxdepth.png)        