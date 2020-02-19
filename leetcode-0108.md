## 思路
- 递归
- 对于一个排序数组，使其mid位置的数组作为根节点[0,mid-1]作为左子树，[mid+1,end]作为右子树
- 递归结束的条件是strt>end 或者 start=end

```java
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        if(nums==null) return null;
        return helper(nums, 0, nums.length-1);
    }

    private TreeNode helper(int[] nums, int start, int end){
        if(start>end) return null;
        if(start==end) return new TreeNode(nums[start]);
        int mid = (start+end)/2;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = helper(nums, start, mid-1);
        root.right = helper(nums, mid+1, end);
        return root;
    }
}
```