## 思路
- 使用preHead作为listNode的前缀
- 假设加了preHead之后listNode为 `0->1->2->3->4->null` ,使用四个指针，left和right分别指向要交换的两个，pre和next指向要前和后，于是就有了
```
  0->   1->   2->   3->4->null
  |     |     |     |
  pre  left  right next
```
- 每次循环交换left和right指向的node，循环终止的场景为 `next==null(双数长度链表)` 或者 `next.next==null(单数长度链表)` 

```java
class Solution {
    public ListNode swapPairs(ListNode head) {
        if(head==null || head.next==null){
            return head;
        }
        ListNode preHead = new ListNode(0);
        ListNode pre = preHead;
        preHead.next = head;
        ListNode left = head;
        ListNode right = head.next;
        ListNode next = right.next;
        while(right!=null){
            right.next = left;
            left.next = next;
            pre.next = right;

            if(next==null || next.next==null){
                break;
            }
            pre = left;
            left = next;
            right = next.next;
            next = right.next;
        }
        return preHead.next;
    }
}
```