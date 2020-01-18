## 思路
- 动态规划
- 使用一个数组dp[n]记录当以i为结尾时的最大子序列和，那么就有状态转移方程：`dp[i]=max(dp[i-1]+nums[i], nums[i])`
- 每一次获取i位置时的dp[i]的时候和当前最大的子序列和比较，更新最大子序列和

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int ans = nums[0];
        int[] dp = new int[nums.length];
        dp[0]=nums[0];
        for(int i=1; i<nums.length; i++){
            dp[i] = Math.max(dp[i-1]+nums[i], nums[i]);
            ans = Math.max(ans, dp[i]);
        }
        return ans;
    }
}
```