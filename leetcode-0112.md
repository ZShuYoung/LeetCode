## 思路
- 递归
- 终止条件是root==null 或root是叶子切值等于或者不等于sum

```java
class Solution {
    public boolean hasPathSum(TreeNode root, int sum) {
        if(root==null) return false;
        if(root.left==null && root.right==null){
            if(root.val==sum){
                return true;
            }else{
                return false;
            }
        }
        return hasPathSum(root.left, sum-root.val) || hasPathSum(root.right, sum-root.val);
    }
}
```