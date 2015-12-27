title: "LeetCode:Merge Two Sorted Lists"
date: 2015-07-29 10:31:25
tags: [算法,LeetCode]
---

##题目

  [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

   有两个排序好的链表l1和l2，要求是合并为一个列表，并保持列表有序。
        
##思路
    
   我的想法是先遍历两个链表找到较短的一个，然后把短链表上节点逐个插入到长链表中。
    
   然后在网上看别人的代码，其实不用先找到短链。拿一个链表做基准，将另外一个插入就来，只遍历一次就好了。

##实现

JavaScript:

    /**
     * Definition for singly-linked list.
     * function ListNode(val) {
     *     this.val = val;
     *     this.next = null;
     * }
     */
    /**
     * @param {ListNode} l1
     * @param {ListNode} l2
     * @return {ListNode}
     */
    var mergeTwoLists = function(l1, l2) {
        //定义指针
        var sPointer = l1,lPointer = l2;
    
        //一些特殊情况的处理
        if(sPointer&&sPointer.val&&lPointer&&lPointer.val===null){
            return sPointer;
        }
        if(sPointer&&sPointer.val===null&&lPointer&&lPointer.val){
            return lPointer;
        }
        if(sPointer&&!lPointer){
            return sPointer;
        }
        if(!sPointer&&lPointer){
            return lPointer;
        }
        if(!sPointer&&!lPointer){
            return null;
        }
        
         //找到较短链表,逐个插入到长链表中
        while(sPointer){
            if(!lPointer){ //lpointer为null，说明l1>l2
                sPointer = l2;
                lPointer = l1;
                break;
            }
            sPointer = sPointer.next;
            lPointer = lPointer.next;
        }
        if(!sPointer){
            //l1<=l2
            sPointer = l1;
            lPointer = l2;
        }
    
        //为了保存插入节点previous的位置，创建一个dummy的节点
        var dummy = new ListNode(0);
        dummy.next = lPointer;
    
        var prePointer = dummy;
    
        var insertnode = sPointer;
        while(sPointer){
            if(insertnode.val<=lPointer.val){
    
                prePointer.next = insertnode;
                sPointer = sPointer.next;
                insertnode.next = lPointer;
                //短链的指针后移一位，长链不动
                insertnode = sPointer;
                prePointer = prePointer.next;
            }else{
                if(!lPointer.next){
                    lPointer.next = sPointer;
                    break;
                }
                //长链后移一位，短链不动
                prePointer =lPointer;
                lPointer = lPointer.next;
            }
    
    
        }
        return dummy.next;
    };
    
 
  ![merge2sortedlists](/images/merge2sortedlists.png)