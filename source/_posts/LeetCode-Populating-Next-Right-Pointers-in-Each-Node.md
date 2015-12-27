title: "LeetCode Populating Next Right Pointers in Each Node"
date: 2015-10-12 15:22:17
tags: [算法, LeetCode]
---

##题目

[Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

给一个平衡二叉树的每个节点加上next属性,next 指向起相邻的节点，如果没有则指向null;

Given the following perfect binary tree,

             1
           /  \
          2    3
         / \  / \
        4  5  6  7
    
After calling your function, the tree should look like:

             1 -> NULL
           /  \
          2 -> 3 -> NULL
         / \  / \
        4->5->6->7 -> NULL
    
    
##思路
    
   1.对于一个父节点来说，它左孩子的next指向它的右孩子，它的右孩子的next指向它自己next节点的左孩子。
   2.遍历整个二叉树，对每个父节点进行1操作。
    
   
##实现
    
JavaScript:
    
    /**
     * Definition for binary tree with next pointer.
     * function TreeLinkNode(val) {
     *     this.val = val;
     *     this.left = this.right = this.next = null;
     * }
     */
    
    /**
     * @param {TreeLinkNode} root
     * @return {void} Do not return anything, modify tree in-place instead.
     */
    var connect = function(root) {
        if(root===null) return;
        root.next =null;
        
        
        function traversal(node){
            if(node){
                if(node.left){
                    connectLeftChild(node,node.left);
                    traversal(node.left);
                }
                if(node.right){
                    connectRightChild(node,node.right);
                    traversal(node.right);
                }
            }
            
            
        }
        function connectLeftChild(parent,node){
            
            if(node){
                 node.next = parent.right;
            }
        } 
        function connectRightChild(parent,node){
            if(node){
                if(parent.next){
                    node.next = parent.next.left;
                }else{
                    node.next = null;
                }
                
            }
            
        }
        traversal(root);
    };
    
##耗时
    
  ![nextpointerruntime](/images/nextpointer.png)