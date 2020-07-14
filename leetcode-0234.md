## 思路

1. 涉及回文考虑快慢指针第一种做法用栈来辅助记录前面的一半
2. 第二种翻转后一半链表之后再与前一半作比较

```java
class Solution {

    public boolean isPalindrome(ListNode head) {
        if(head==null || head.next==null) return true;
        ListNode preHead = new ListNode(0);
        preHead.next = head;
        ListNode slow = preHead;
        ListNode fast = preHead;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            fast = fast.next.next;
        }
        slow.next = reverse(slow.next);
        slow = slow.next;
        fast = head;
        while(slow!=null){
            if(slow.val != fast.val){
                return false;
            }
            slow = slow.next;
            fast = fast.next;
        }
        return true;
    }

    private ListNode reverse(ListNode ptr){
        if(ptr==null || ptr.next==null){
            return ptr;
        }
        ListNode cur = ptr;
        ListNode nex = cur.next;
        ListNode nn = nex.next;
        cur.next = null;
        while(nex != null){
            nex.next = cur;
            cur = nex;
            nex = nn;
            if(nn!=null){
                nn = nn.next;
            }
        }
        return cur;

    }

    public boolean isPalindrome2(ListNode head) {
        if(head==null) return true;
        Deque<Integer> stack = new ArrayDeque<>();
        ListNode preHead = new ListNode(0);
        preHead.next = head;
        ListNode slow = preHead;
        ListNode fast = preHead;
        while(fast!=null && fast.next!=null){
            slow = slow.next;
            stack.push(slow.val);
            fast = fast.next.next;
        }
        if(fast==null){
            stack.pop();
        }
        slow = slow.next;
        while(slow!=null){
            if(stack.pop()!=slow.val){
                return false;
            }
            slow=slow.next;
        }
        return true;
    }
}
```