## 思路
- 和#82基本一致，用ptr指向消除重复之后的数组最后一位，next指向有可能的下一位
- 最后把ptr.next置为null

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
        ListNode ptr = head;
        ListNode next = head.next;
        while(next!=null){
            if(ptr.val!=next.val){
                ptr.next=next;
                ptr=next;
                next=next.next;
            }else{
                next=next.next;
            }
        }
        ptr.next=null;
        return head;
    }
}
```