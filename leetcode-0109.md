## 思路
- 和#108一样的思路，需要找到链表的mid位置，怎么找链表的mid位置可以用快慢指针
- 所以继续用递归，这是这里需要的技巧是递归结束的判断
- helper方法的第一个参数是链表头，第二个是链表位（不包含）。所以当head=destination的时候返回null;当head.next=destination的时候说明只有一个节点了，直接返回一个TreeNode

```java
class Solution {
    public TreeNode sortedListToBST(ListNode head) {
        if(head==null) return null;
        if(head.next==null) return new TreeNode(head.val);
        return helper(head, null);
    }

    private TreeNode helper(ListNode head, ListNode destination){
        if(head==destination) return null;
        if(head.next==destination) return new TreeNode(head.val);
        ListNode fast = head;
        ListNode slow = head;
        while(fast!=destination && fast.next!=destination){
            slow = slow.next;
            fast = fast.next.next;
        }
        TreeNode root = new TreeNode(slow.val);
        root.left = helper(head, slow);
        root.right = helper(slow.next, destination);
        return root;
    }
}
```