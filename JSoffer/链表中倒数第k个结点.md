#链表中倒数第k个结点

##题目描述

输入一个链表，输出该链表中倒数第k个结点。


```
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/

public class Solution {
    public ListNode FindKthToTail(ListNode head, int k) {
        if(head == null || k<=0){
            return null;
        }
        ListNode pre = head;
        ListNode last = head;
        for(int i = 1; i < k;i++){
            if(last.next != null){
                last = last.next;
            }else{
                return null;
            }
        }
        while(last.next != null){
            last = last.next;
            pre = pre.next;
        }
        return pre;
    }
}
```
