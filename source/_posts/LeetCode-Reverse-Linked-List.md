title: "LeetCode:Reverse Linked List"
date: 2015-08-04 10:40:27
tags: [算法,LeetCode]
---

##题目Topic

反转链表
[Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

##思路How to

递归实现，先反转head后面的链表，这时原来的第二个节点(head->next)已经移到链尾了，把head赋给原来第二个节点的next，并以原head收尾，实现反转。

##实现 Implementation

JavaScript:

       /**
        * 递归实现
        * @param {ListNode} head
        * @return {ListNode}
        */
       var reverseList = function(head) {
           if(head===null||head.next===null){
               return head;
           }else{
               var newHead = reverseList(head.next);
               head.next.next = head;
               head.next=null;
               return newHead;
           }
       };

##耗时

![reverselist](/images/reverselist.png)