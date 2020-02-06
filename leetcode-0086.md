## 思路
- 用一个left记录值小于x的节点；用一个right记录值大于等于x的节点
- 最后pr.next=null   pl.next=right.next
  
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
    public ListNode partition(ListNode head, int x) {
        if(head==null || head.next==null) return head;
        ListNode left = new ListNode(0);
        ListNode right = new ListNode(0);
        ListNode pl = left;
        ListNode pr = right;
        while(head!=null){
            if(head.val<x){
                pl.next=head;
                pl=head;
            }else{
                pr.next=head;
                pr=head;
            }
            head=head.next;
        }
        pr.next=null;
        pl.next=right.next;
        return left.next;
    }
}
```