## 思路
- 递归

```
我们只需要把 1 作为根节点，[ ] 空作为左子树，[ 2 ... n ] 的所有可能作为右子树。
2 作为根节点，[ 1 ] 作为左子树，[ 3...n ] 的所有可能作为右子树。
3 作为根节点，[ 1 2 ] 的所有可能作为左子树，[ 4 ... n ] 的所有可能作为右子树，然后左子树和右子树两两组合。
4 作为根节点，[ 1 2 3 ] 的所有可能作为左子树，[ 5 ... n ] 的所有可能作为右子树，然后左子树和右子树两两组合。
...
n 作为根节点，[ 1... n ] 的所有可能作为左子树，[ ] 作为右子树。

如果只有一个数字，那么所有可能就是一种情况，把该数字作为一棵树。而如果是 [ ]，那就返回 null。
```

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<TreeNode> generateTrees(int n) {
        if(n==0){
            List<TreeNode> ans = new LinkedList<>();
            return ans;
        }
        return generate(1, n);
    }

    private List<TreeNode> generate(int start, int end) {
        if(start>end){
            List<TreeNode> ans = new LinkedList<>();
            ans.add(null);
            return ans;
        }
        if(start==end){
            List<TreeNode> ans = new LinkedList<>();
            ans.add(new TreeNode(start));
            return ans;
        }

        List<TreeNode> ans = new LinkedList<>();
        for(int i=start; i<=end; i++){
            List<TreeNode> left = generate(start, i-1);
            List<TreeNode> right = generate(i+1, end);

            for(TreeNode l : left){
                for(TreeNode r : right){
                    TreeNode root = new TreeNode(i);
                    root.left = l;
                    root.right = r;
                    ans.add(root);
                }
            }
        }
        return ans;
    }
}
```