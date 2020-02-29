## 思路
- 对于环形链表来说，有两种情况，要么跑到null要么一直在循环走不到null
- 所以用快慢指针

```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode walker = head;
        ListNode runner = head;
        while(runner!=null && runner.next!=null){
            walker = walker.next;
            runner = runner.next.next;
            if(walker==runner){
                return true;
            }
        }
        return false;
    }
}
```