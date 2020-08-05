## 思路
- 动态规划：记`dp[i]`表示到位置i为止所能获取的最大收益，对于第i天来说，只有偷和不偷两种选择。
- 如果不偷：`dp[i]=dp[i-1]`
- 如果偷：那么第i-1天就不能偷，则有`dp[i-1]=dp[i-2]`，所以`dp[i]=dp[i-2]+nums[i]`
- 综上获取状态转移方程`dp[i] = Math.max(dp[i-1], dp[i-2]+nums[j])`

```java
class Solution {
    public int rob(int[] nums) {
        if(nums==null || nums.length==0) return 0;
        int[] dp = new int[nums.length+1];
        dp[0]=0;
        dp[1]=nums[0];
        for(int i=2; i<dp.length; i++){
            int j=i-1;
            dp[i] = Math.max(dp[i-1], dp[i-2]+nums[j]);
        }
        return dp[dp.length-1];
    }
}
```