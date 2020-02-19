## 思路
- 这里和求最大深度不一样，`最小深度是从根节点到最近叶子节点的最短路径上的节点数量。` 所以对于某个子树为null，要取其不为null的子树的最小深度在加1

```java
class Solution {
    public int minDepth(TreeNode root) {
        if(root==null) return 0;
        if(root.left==null && root.right==null) return 1;
        if(root.left!=null && root.right==null) return minDepth(root.left) + 1;
        if(root.left==null && root.right!=null) return minDepth(root.right) + 1;
        return Math.min(minDepth(root.left), minDepth(root.right)) + 1;
    }
}
```