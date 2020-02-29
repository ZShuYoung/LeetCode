## 思路
- 本题和#141相似，只是在找成点的位置有区别
- 还是快慢指针，记head到环的距离为a，环点到相遇点的距离为b，相遇点到环点的距离为c，那么就有 `2*(a+b)=a+2b+c` ， 得到 `a=c` 即head到成环点和快慢指针相遇点到成环点的距离是一样的。那么当快慢指针相遇的时候，安排一个指针从头，另一个指针从相遇点开始每次走一步，相遇点即为成环点

```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode walker = head;
        ListNode runner = head;
        while(runner!=null && runner.next!=null){
            walker = walker.next;
            runner = runner.next.next;
            // 和#141不一样的逻辑就在找成环点的位置
            if(walker==runner){
                walker = head;
                while(walker!=runner){
                    walker=walker.next;
                    runner=runner.next;
                }
                return walker;
            }
        }
        return null;
    }
}
```