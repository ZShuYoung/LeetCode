## 思路
- 动态规划：记录dp[i]表示索引i为终点的子字符串能否在分割成wordDict中的字符，那么对于任何j[0,i)，只要dp[j]为true且[j,i)的子串包含在wordDict中，那么dp[i]则为true

```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        boolean[] dp = new boolean[s.length()+1];
        dp[0] = true;
        // i从1开始表示子串取不到endIndex
        for(int i=1; i<=s.length(); i++){
            // j从0开始要保证s能取到第一个字符作为子字符串
            for(int j=0; j<i; j++){
                if(dp[j] && wordDict.contains(s.substring(j,i))){
                    dp[i] = true;
                    break;
                }
            }
        }
        return dp[dp.length-1];
    }
}
```