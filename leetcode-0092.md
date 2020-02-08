## 思路
- 两个指针，先根据m和n找到要翻转的那部分
- 单独把反转的那部分拎出来，翻转，再联回原来的链表

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
    public ListNode reverseBetween(ListNode head, int m, int n) {
        if(m==n) return head;
        ListNode preHead = new ListNode(0);
        ListNode ptr = preHead;
        ptr.next = head;
        ListNode p1 = ptr;
        ListNode p2 = ptr;
        int move1 = m-1;
        int move2 = n-1;
        while(move1 != 0){
            p1 = p1.next;
            move1--;
        }
        while(move2 != 0){
            p2 = p2.next;
            move2--;
        }
        ListNode start = p1.next;
        ListNode end = p2.next;
        p2 = end.next;
        end.next = null;
        ListNode rv = reverse(start);
        p1.next.next = p2;
        p1.next = rv;
        return preHead.next;

    }

    public ListNode reverse(ListNode start){
        if(start == null || start.next == null) return start;
        ListNode pre = new ListNode(-1);
        pre.next = start;
        ListNode ptr = pre;
        ListNode next = start.next;
        ListNode nextNext = next.next;
        while(nextNext != null){
            next.next = start;
            start = next;
            next = nextNext;
            nextNext = nextNext.next;
        }
        next.next = start;
        return next;
    }
}
```