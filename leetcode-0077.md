## 思路
- 回溯
- 和全排列的思路基本一致

```java
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> ans = new LinkedList<>();
        List<Integer> one = new LinkedList<>();
        backTrack(ans, one, n, k, 1);
        return ans;
    }

    private void backTrack(List<List<Integer>> ans, List<Integer> one, int n, int k, int start){
        if(one.size() == k){
            ans.add(new LinkedList<Integer>(one));
            return;
        }else{
            for(int i=start; i<=n; i++){
                one.add(i);
                backTrack(ans, one, n, k, i+1);
                one.remove(one.size()-1);
            }
        }
    }
}
```