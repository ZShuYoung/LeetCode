## 思路
- 回溯法
- 对于candidates = [2,3,6,7], target = 7这种，从第一个2开始，直到发现[2,2,2,2]不满足条件了，则退出到[2,2,2]
- 再从3开始，[3,6]退出到[3],再到[3,7]不满足退出

```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> one = new ArrayList<>();
        backtrack(ans, one, candidates, target, 0);
        return ans;
    }

    private void backtrack(List<List<Integer>> ans, List<Integer> one, int[] candidates, int remain, int start){
        if(remain==0){
            ans.add(new ArrayList<Integer>(one));
            return;
        }
        for(int i=start; i<candidates.length && remain>0; i++){
            one.add(candidates[i]);
            backtrack(ans, one, candidates, remain-candidates[i], i);
            one.remove(one.size()-1);
        }
    }
}
```