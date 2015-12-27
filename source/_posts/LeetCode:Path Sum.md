title: "LeetCode:Path-Sum"
date: 2015-07-19 22:37:32
tags: [算法,LeetCode]
---

##题目来源
 [指定和值的二叉树路径查找](https://leetcode.com/problems/path-sum/)
 
 现在有一个二叉树，找出这个二叉树中是否有存在这样一条根到叶子的路径能使路径节点上的值加起来等于给定的值。
 *比如*下面这个二叉树，给定的值是22，5->4->11->2 这条路径是满足条件的。
 
               5
              / \
             4   8
            /   / \
           11  13  4
          /  \      \
         7    2      1


##思路
 这就是一个二叉树遍历，从根节点往下，每找到一个节点将节点的value和当前路径相加，判断是否和sum相等。
  * 如果相等，并且是叶子节点，则返回true，找到
  * 如果不相等，相等但不是叶子节点，则继续查找，直到所有的节点都遍历过。
  
##实现
     
 JavaScript:
      
      var checkNext =function(root, sum, currentSum,flag){
          if (root) {
      
              if (root.val + currentSum === sum) {
                  if (root.left === null && root.right === null) {
                      return true;
                  }
              }
              if(root.left===null&&root.right===null){
                  return false;
              }
      
              if (root.left !== null) {
                  flag = checkNext(root.left, sum, root.val + currentSum,flag);
              }
              if(flag){
                  return true;
              }
              if (root.right !== null) {
                  flag = checkNext(root.right, sum, root.val + currentSum,flag);
              }
              return flag;
      
      
          } else {
              return false;
          }
      }
      var hasPathSum = function (root, sum) {
      
          if(checkNext(root, sum, 0,false)){
              return true
          }else{
              return false
          }
        };

 

PS:这是我在leetcode上做的第一个题，最初没有搞明白玩法，一直在自己实现二叉树，后面才发现原来二叉树已经写好，只要给遍历方法就好了。

![Runtime](/images/pathsumruntime.png)