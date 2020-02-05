## 思路
- 用两个指针pre和next遍历整个链表
- 当pre和next值不等的时候，将pre所指节点放入待返回的链表中；pre和next分别后移
- 当pre和next相等的时候，不断后移next直到next指向null或者出现值不一致。
- 如果next为null了，说明从pre开始的值都是重复的，直接ptr.next=null 返回链表；对应`0->1->2->3->3`这种场景
- 如果next不为null，将pre移到该点，next指向其后一点，再次循环
- 如果循环结束，则需要带上pre指向的点

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if(head==null || head.next==null) return head;
        ListNode preHead = new ListNode(0);
        ListNode ptr = preHead;
        ListNode pre = head;
        ListNode next = head.next;
        while(next!=null){
            if(pre.val!=next.val){
                ptr.next=pre;
                ptr=pre;
                pre=next;
                next=next.next;
            }else{
                while(next!=null && next.val==pre.val){
                    next=next.next;
                }
                if(next==null){
                    ptr.next=null;
                    return preHead.next;
                }
                pre=next;
                next=pre.next;
            }
        }
        ptr.next=pre;
        return preHead.next;
    }
}
```