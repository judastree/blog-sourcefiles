title: "LeetCode:Intersection of Two Linked Lists"
date: 2015-07-24 10:47:40
tags: [算法, LeetCode]
---

##题目

[查找两个链表相同的尾链](https://leetcode.com/problems/intersection-of-two-linked-lists/)

    A:          a1 → a2
                       ↘
                         c1 → c2 → c3
                       ↗            
    B:     b1 → b2 → b3
    
 *如果两个链表没有相同尾链，返回null。
 *两个链表在输出时应保持原来的结构。
 *链表结构中没有循环。
 *时间复杂度要求O(n),空间复杂度要求O(1)
 
##思路

 先取A，B链的长度，找出哪个是短链，哪个是长链。
 
 然后找到长链尾部和短链长度相同的位置，开始比较它和短链是否相等。
 
 如果当前节点不相等，则两者后移一位继续比较，直到找到第一个相等的节点，记录之。
 
 如果当前节点不相等，但前一个节点相等，说明没有相同的尾链，返回null。
 
 
## 实现

JavaScript:

        /**
         * @param {ListNode} headA
         * @param {ListNode} headB
         * @return {ListNode}
         */
        var getIntersectionNode = function(headA, headB) {
        
            if(headA&&headB){
                var node=headA,aLength=1,bLength=1;
                while(node.next){
                    aLength++;
                    node = node.next;
                }
                node= headB;
                while(node.next){
                    bLength++;
                    node=node.next;
                }
                var pointer1 ,pointer2;
                //将ab链截取到尾部位数相同
                if(aLength > bLength){
                    pointer1 = headB;
                    pointer2 = headA;
                    for(var i = bLength;i<aLength;i++){
                        pointer2 = pointer2.next;
                    }
                }else if(aLength<bLength){
                    pointer1 = headA;
                    pointer2 = headB;
                    for(i = aLength;i<bLength;i++){
                        pointer2 = pointer2.next;
                    }
                }else{
                    pointer1 = headA;
                    pointer2 = headB;
                }
        
                node = null;
                //保留上次比较结果
                var sameFlag = false;
                while(pointer1){
        
                    if(pointer1.val===pointer2.val){
                        //当前相等，继续比较。
                        // 如果上次比较不相等，则赋值node，说明是第一个相等的节点
                        if(!sameFlag){
                            node = pointer1;
                        }
                        sameFlag=true;
                        pointer1 = pointer1.next;
                        pointer2 = pointer2.next;
                        continue;
        
                    }
                    if(pointer1.val!==pointer2.val){
                        //当前不相等，判断上次比较是否相等。
                        if(sameFlag){
                            //上次比较相等，则直接返回null，说明没有相同的尾链
                            return null;
                        }else{
                            //上次比较不相等，则继续比较
                            pointer1 = pointer1.next;
                            pointer2 = pointer2.next;
                            sameFlag=false;
                            continue;
                        }
        
                    }
                }
                return node;
        
            }else{
                return null;
            }
        };
 
 
 
 ![intersection](/images/intersection.png)