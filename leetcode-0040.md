## 思路
- 回溯法
- 和39题不一样的是不能重复使用了，所以在回溯的时候需要在位置i的地方加1

```java
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
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
            if(i>start && candidates[i]==candidates[i-1]){
                continue;
            }
            one.add(candidates[i]);
            backtrack(ans, one, candidates, remain-candidates[i], i+1);
            one.remove(one.size()-1);
        }
    }
}
```