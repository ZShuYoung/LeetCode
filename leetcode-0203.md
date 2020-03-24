

```java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        if(head==null) return null;
        ListNode preHead = new ListNode(0);
        preHead.next = head;
        ListNode pre = preHead;
        while(pre != null && pre.next != null){
            ListNode cur = pre.next;
            while(cur != null && cur.val == val){
                cur = cur.next;
            }
            pre.next = cur;
            pre = cur;
        }
        return preHead.next;
    }
}
```