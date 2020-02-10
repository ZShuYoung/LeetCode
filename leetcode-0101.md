## 思路
### 递归
- 递归终止的条件是左右子树都为null，那么肯定是镜像的；子树两次不一致或者值不相等就退出不是镜像
- 子树的左子树和子树的右子树镜像；左子树的右子树和右子树的左子树互为镜像

```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root==null) return true;
        return helper(root.left, root.right);
    }

    private boolean helper(TreeNode left, TreeNode right){
        if(left== null || right==null){
            return left==right;
        }
        if(left.val != right.val){
            return false;
        }
        return helper(left.left, right.right) && helper(left.right, right.left);
    }
}
```

### 迭代
- 用一个栈来存放左右子树，每次迭代的时候取出栈首两个节点，判断是否互为镜像
- 互为镜像之后再判断两个节点各自的左右子树
```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root==null) return true;
        Stack<TreeNode> stack = new Stack<>();
        stack.push(root.right);
        stack.push(root.left);
        while(!stack.isEmpty()){
            TreeNode left = stack.pop();
            TreeNode right = stack.pop();
            if(left==null && right==null){
                continue;
            }
            if((left==null && right!=null) || (left!=null && right==null)){
                return false;
            }
            if(left.val != right.val){
                return false;
            }
            // 这里按照镜像对称塞进栈内
            stack.push(right.right);
            stack.push(left.left);
            stack.push(right.left);
            stack.push(left.right);
        }
        return true;
    }
}
```