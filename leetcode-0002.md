## 基本思路
1. 但凡l1或l2或者有进位，则需要新增一个node，所以有了最外层的while循环
2. 循环内部对每一个合node做处理
   - l1为不为null
   - l2为不为null
   - 上一次进位的值


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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode preNode = new ListNode(0);
        ListNode ptr = preNode;
        int carry = 0;
        while( l1!=null || l2!=null || carry!=0){
            int num1 = l1==null ? 0 : l1.val;
            int num2 = l2==null ? 0 : l2.val;
            int sum = num1+num2+carry;
            int current = sum%10;
            carry = sum/10;
            ListNode currentNode = new ListNode(current);
            ptr.next = currentNode;
            ptr = currentNode;
            l1 = l1==null ? null : l1.next;
            l2 = l2==null ? null : l2.next;
        }
        return preNode.next;
    }
}
```