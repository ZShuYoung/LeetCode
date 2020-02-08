## 基础算法——二叉树的中序遍历

```java
class Solution {
    // 递归
    public List<Integer> inorderTraversal(TreeNode root) {
        if(root==null){
            return new LinkedList<Integer>();
        }
        List<Integer> ans = new LinkedList<>();
        List<Integer> left = inorderTraversal(root.left);
        List<Integer> right = inorderTraversal(root.right);
        ans.addAll(left);
        ans.add(root.val);
        ans.addAll(right);
        return ans;
    }

    // 非递归
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> ans = new LinkedList<>();
        Stack<TreeNode> stack = new Stack<>();
        TreeNode cur = root;
        while(cur != null || !stack.isEmpty()){
            while(cur!=null){
                stack.push(cur);
                cur = cur.left;
            }
            if(!stack.isEmpty()){
                cur = stack.pop();
                ans.add(cur.val);
                cur = cur.right;
            }
        }
        return ans;
    }
}
```