## 思路
### 递归
- 递归结束点是结点为null，那么深度为0；否则是子树深度加1；这里要去左右子树的大值

```java
class Solution {
    public int maxDepth(TreeNode root) {
        if(root==null) return 0;
        return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1;
    }
}
```

### 递归
- 这里求的是最大深度，用BFS去考虑，用队列记录每层的结点，思路同#102和#103。因为每一层循环都是一层
```java
class Solution {
    public int maxDepth(TreeNode root) {
        if(root==null) return 0;
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);

        int level = 0;
        while(!q.isEmpty()){
            int levelNumber = q.size();
            for(int i=0; i<levelNumber; i++){
                TreeNode temp = q.poll();
                if(temp.left!=null) q.add(temp.left);
                if(temp.right!=null) q.add(temp.right);
            }
            level++;
        }
        return level;
    }
}
```
