## 思路
- 递归

```java
class Solution {
    public int sumNumbers(TreeNode root) {
        return helper(root, 0);
    }

    private int helper(TreeNode node, int tempSum){
        if(node==null) return 0;
        if(node.left==null && node.right==null){
            return tempSum*10 + node.val;
        }
        return helper(node.left, tempSum*10 + node.val) + helper(node.right, tempSum*10 + node.val);
    }
}
```



- 迭代
```java
class Solution {
    public int sumNumbers(TreeNode root) {
        if(root == null){
            return 0;
        }
        Stack<TreeNode> nodeStack = new Stack<>();
        Stack<String> nodePath = new Stack<>();
        nodeStack.push(root);
        nodePath.push(""+root.val);
        int runningSum = 0;
        while(!nodeStack.isEmpty()){
            TreeNode node = nodeStack.pop();
            String currentPath = nodePath.pop();
            if(node.right != null){
                nodeStack.push(node.right);
                nodePath.push(currentPath + (""+node.right.val));
            }
            if(node.left != null){
                nodeStack.push(node.left);
                nodePath.push(currentPath+ (""+ node.left.val) );
            }
            if( node.left == null && node.right == null){
                runningSum = runningSum + Integer.valueOf(currentPath);
            }
            
        }
        return runningSum;
        
    }
}
```