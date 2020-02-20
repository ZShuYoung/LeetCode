## 思路
- 回溯算法，和之前的回溯算法套路基本一致

```java
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> one = new ArrayList<>();
        backTrack(root, sum, ans, one);
        return ans;
    }

    private void backTrack(TreeNode root, int sum, List<List<Integer>> ans, List<Integer> one){
        if(root==null) return;
        one.add(root.val);
        if(root.left==null && root.right==null && root.val==sum){
            ans.add(new ArrayList(one));
        }else{
            backTrack(root.left, sum-root.val, ans, one);
            backTrack(root.right, sum-root.val, ans, one);
        }
        one.remove(one.size()-1); //最后删掉
    }
}
```