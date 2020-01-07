## 思路
- 两次遍历，去一个preHead节点
- 第一次遍历，记录下来长度length
- 第二次遍历，从preHead开始往后，移动(length-n)步，则当前节点的下一个节点即为待删除节点

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode preHead = new ListNode(0);
        ListNode ptr = preHead;
        ptr.next = head;
        int length = 0;
        while(ptr.next != null){
            length++;
            ptr = ptr.next;
        }
        ptr = preHead;
        int move = length - n;
        while(move!=0){
            ptr = ptr.next;
            move--;
        }
        ptr.next = ptr.next.next;
        return preHead.next;
    }
}
```