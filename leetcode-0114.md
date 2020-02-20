## 思路
- 递归，按照下面三个步骤
- 终止条件是root==null 直接返回
- 分别用left和right指向左右子树，再平铺左右子树
- 这时候将铺好的左子树接到root右边，再找到末尾，将平铺好的右子树接上

```java
class Solution {
    public void flatten(TreeNode root) {
        if(root==null) return;
        TreeNode left = root.left;
        TreeNode right = root.right;

        flatten(root.left);
        flatten(root.right);

        root.left=null;
        root.right=left;
        TreeNode ptr = root;
        while(ptr.right!=null){
            ptr=ptr.right;
        }
        ptr.right=right;
        return;
    }
}
```