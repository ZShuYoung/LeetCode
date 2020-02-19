## 思路
- 和前面的一样，这是这里每层记录的level都塞在数组的第一个的位置

```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> ans = new LinkedList<>();
        if(root==null) return ans;
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        while(!q.isEmpty()){
            int size = q.size();
            List<Integer> level = new LinkedList<>();
            for(int i=0; i<size; i++){
                TreeNode top = q.poll();
                level.add(top.val);
                if(top.left!=null) q.add(top.left);
                if(top.right!=null) q.add(top.right);
            }
            // 和基本的层序遍历只有这里不一样
            ans.add(0, level);
        }
        return ans;
    }
}
```