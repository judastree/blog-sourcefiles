title: "LeetCode:Palindrome Linked List"
date: 2015-07-26 00:03:00
tags: [LeetCode,算法]
---

##题目

[Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

判断一个单向链表（没有环）是否是回文链表。

要求时间复杂度在O(n),空间复杂度 O(1)

##思路

    1, 找到链表的中间节点。
    2, 反转链表后半部分。
    3, 比较前半部分和后半部分的值是否相等
    4, 还原现场，将后半部分反转回原貌
    
##查到链表的中间节点    

            var fPointer = sPointer = midPos= head;
            while (fPointer.next) {
                sPointer = sPointer.next;
                fPointer = fPointer.next;
                if(fPointer.next){
                    fPointer = fPointer.next;
                }else{
                    break;
                }
            }
            midPos = sPointer;
                
##反转链表


PS: 反转还没有写出来，下面是错误的。

  反转链表的方法是从第2个节点到第N个节点，依次逐节点插入到第1个节点(head节点)之后，最后将第一个节点挪到新表的表尾。
  
  我们此时的head是midPos,移动sPointer指针。
    
    fPointer = misPos;
    sPointer = sPointer.next;
    
    while(sPointer){
        //暂时保存head.next
        fPointer = midPos.next;
        //将要插入的节点放到head的next
        midPos.next = sPointer;
        //将插入节点的next赋值为前面保存的head.next
        sPointer.next = fPointer;
        
        //移动sPointer
        sPointer = sPointer.next   
    }
    
    
    
