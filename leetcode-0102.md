## 思路
- 用一个队列记录每一层的结点，循环条件是队列不为空
- 每一次循环都记录下来一层的结点，并且依次将下一层的结点都塞入队列；每次循环开头先记录队列当前队列长度，即为当前层的结点数

```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> ans = new LinkedList<>();
        if(root==null) return ans;
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);

        while(!q.isEmpty()){
            // 这里要记录levelNumber,因为循环中会不断往队列塞下一层的结点
            int levelNumber = q.size();
            List<Integer> level = new LinkedList<>();
            for(int i=0; i<levelNumber; i++){
                TreeNode temp = q.poll();
                level.add(temp.val);
                if(temp.left!=null){
                    q.add(temp.left);
                }
                if(temp.right!=null){
                    q.add(temp.right);
                }
            }
            ans.add(level);
        }
        return ans;
    }
}
```