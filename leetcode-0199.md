## 思路
- 使用层序遍历，将每一层最后一个结点的值记入list即可

```java
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> ans = new LinkedList<>();
        if(root==null) return ans;
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        while(!q.isEmpty()){
            int size = q.size();
            for(int i=0; i<size-1; i++){
                TreeNode cur = q.poll();
                if(cur.left!=null) q.add(cur.left);
                if(cur.right!=null) q.add(cur.right);
            }
            TreeNode levelLast = q.poll();
            ans.add(levelLast.val);
            if(levelLast.left!=null) q.add(levelLast.left);
            if(levelLast.right!=null) q.add(levelLast.right);
        }
        return ans;
    }
}
```