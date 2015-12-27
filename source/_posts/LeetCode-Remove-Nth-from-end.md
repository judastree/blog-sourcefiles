title: "LeetCode:Remove Nth Node from End of List"
date: 2015-08-07 09:07:42
tags: [LeetCode, 算法]
---

##题目

[Remove Nth Node from End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

把倒数第N个元素从链表中删除。

比如链表1->2->3->4->5,  把倒数第二个删除（n=2），返回1->2->3->5

##思路

首先是遍历整个链表，拿到链表的长度，然后根据这个长度值length和指定的n值再遍历一次链表，找到要删除节点的父节点。

##实现

JavaScript:
    
    /**
     * Definition for singly-linked list.
     */
      function ListNode(val) {
          this.val = val;
          this.next = null;
      }
    
    /**
     * @param {ListNode} head
     * @param {number} n
     * @return {ListNode}
     */
    var removeNthFromEnd = function(head, n) {
        var dumy = new ListNode(0), p=head,length=0;
        dumy.next =head;
        //获取链表长度
        while(p){
            length++;
            p = p.next;
        }
        p = dumy;
        //找到要删除元素的父元素
        while(length>n){
            p = p.next;
            length--;
        }
        //删除元素
        if(p.next){
            p.next = p.next.next;
        }else{
            p = null;
        }
        return dumy.next;
    };
    
    
##耗时

![removenthfromend](/images/removenthfromend.png)




