## 思路
- 动态规划
- 和最大连续子系列和思路一致，dp[i]表示以位置i为结尾的连续子序列的最大值，因为这里是乘积，所以除了记录前一个的最大还要记录最小值，防止出现[-2,3,-4]这种情况

```java
class Solution {
    public int maxProduct(int[] nums) {
        if(nums==null || nums.length==0){
            return 0;
        }
        int[] dpMax = new int[nums.length];
        int[] dpMin = new int[nums.length];
        dpMax[0] = nums[0];
        dpMin[0] = nums[0];
        int max = nums[0];
        for(int i=1; i<nums.length; i++){
            dpMax[i] = Math.max(Math.max(dpMax[i-1] * nums[i], dpMin[i-1] * nums[i]), nums[i]);
            dpMin[i] = Math.min(Math.min(dpMax[i-1] * nums[i], dpMin[i-1] * nums[i]), nums[i]);
            max = Math.max(dpMax[i], max);
        }
        return max;
    }
}
```