## 思路
- 和子集思路一致，在遍历的时候跳过和之前重复的值即可

```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);  // 注意先排序
        List<List<Integer>> ans = new LinkedList<>();
        List<Integer> one = new LinkedList<>();
        backTrack(ans, one, nums, 0);
        return ans;
    }

    private void backTrack(List<List<Integer>> ans, List<Integer> one, int[] nums, int start){
        ans.add(new LinkedList<Integer>(one));
        for(int i=start; i<nums.length; i++){
            if(i>start && nums[i-1]==nums[i]){ // 这里多了一次判断
                continue;  
            }
            one.add(nums[i]);
            backTrack(ans, one, nums, i+1);
            one.remove(one.size()-1);
        }
    }
}
```