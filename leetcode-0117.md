## 思路
- 这题不是完美二叉树，但是思路同116，116是通用解法

```java
class Solution {
    public Node connect(Node root) {
        if(root==null) return null;
        Queue<Node> q = new LinkedList<>();
        q.add(root);
        Node pre, cur;
        while(!q.isEmpty()){
            int size = q.size();
            pre = q.poll();
            if(pre.left!=null) q.add(pre.left);
            if(pre.right!=null) q.add(pre.right);
            for(int i=0; i<size-1; i++){
                cur = q.poll();
                pre.next = cur;
                pre = cur;
                if(cur.left!=null) q.add(cur.left);
                if(cur.right!=null) q.add(cur.right);
            }
            pre.next = null;
        }
        return root;
    }
}
```