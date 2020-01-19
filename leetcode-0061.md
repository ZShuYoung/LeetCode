## 思路
- 先遍历一次记录下来整个链表的长度，那么右移k个就是把最右侧的 k%count 个挪到左边

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
    public ListNode rotateRight(ListNode head, int k) {
        if(head==null || head.next==null){
            return head;
        }
        int count=1;
        ListNode ptr = head;
        while(ptr.next!=null){
            count++;
            ptr = ptr.next;
        }
        int move = count - k%count;
        if(move==0){
            return head;
        }
        ListNode preHead = new ListNode(0);
        preHead.next = head;
        ptr = preHead;
        while(move!=0){
            move--;
            ptr = ptr.next;
        }
        preHead.next = ptr.next;
        ptr.next = null;
        ptr = preHead;
        int temp = k%count;
        while(temp!=0){
            ptr = ptr.next;
            temp--;
        }
        ptr.next = head;
        return preHead.next;
    }
}
```
