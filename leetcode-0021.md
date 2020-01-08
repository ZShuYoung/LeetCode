## 思路
- 当l1和l2都不是null的时候，比较大小
- 循环结束，拿不是null的接到尾部

```java
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1==null || l2==null){
            return l1==null ? l2 : l1;
        }
        ListNode preHead = new ListNode(0);
        ListNode ptr = preHead;
        ListNode p1=l1;
        ListNode p2=l2;
        while(p1!=null && p2!=null){
            if(p1.val < p2.val){
                ptr.next = p1;
                p1 = p1.next;
            }else{
                ptr.next = p2;
                p2 = p2.next;
            }
            ptr = ptr.next;
        }
        if(p1!=null){
            ptr.next = p1;
        }
        if(p2!=null){
            ptr.next = p2;
        }
        return preHead.next;
    }
}
```