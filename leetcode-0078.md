## 思路
- 回溯
- 和#77题基本一样，只是在把one添加到ans数组的条件不一样，这里每一次回溯（或者BFS）的时候其实都是一个子集，所以直接加入都ans

```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans = new LinkedList<>();
        List<Integer> one = new LinkedList<>();
        backTrack(ans, one, nums, 0, nums.length);
        return ans;
    }

    private void backTrack(List<List<Integer>> ans, List<Integer> one, int[] nums, int start, int end){
        ans.add(new LinkedList<Integer>(one));
        for(int i=start; i<end; i++){
            one.add(nums[i]);
            backTrack(ans, one, nums, i+1, end);
            one.remove(one.size()-1);
        }
    }
}
```