## 思路
- 和#102题一样，只是记录每一层的结点value的时候用一个标志位判断了一下

```java
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> ans = new LinkedList<>();
        if(root==null) return ans;
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);

        boolean reverseFlag = true;
        while(!q.isEmpty()){
            int levelNumber = q.size();
            List<Integer> level = new LinkedList<>();
            for(int i=0; i<levelNumber; i++){
                TreeNode temp = q.poll();
                // 这里加上了判断
                if(reverseFlag){
                    level.add(temp.val);
                }else{
                    level.add(0, temp.val);
                }
                if(temp.left!=null) q.add(temp.left);
                if(temp.right!=null) q.add(temp.right);
            }
            ans.add(level);
            // 每一次循环代表遍历完了一层，所以这里要翻转一下次序
            reverseFlag = !reverseFlag;
        }
        return ans;
    }
}
```