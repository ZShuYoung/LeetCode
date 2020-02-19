## 思路
- 先判断当前根节点是否是平衡二叉树，在判断左右子节点

```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        if(root==null) return true;
        int leftHeight = height(root.left);
        int rightHright = height(root.right);
        return Math.abs(leftHeight - rightHright) <= 1 && isBalanced(root.left) && isBalanced(root.right);
    }

    private int height(TreeNode root){
        if(root==null) return 0;
        return Math.max(height(root.left), height(root.right)) + 1;
    }
}
```