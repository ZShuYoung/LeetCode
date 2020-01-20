## 思路
- 动态规划
- 使用一个dp[m][n]记录到每个点的路线数，那么就有初始条件 dp[i][0]=1 dp[0][i]=1
- 状态转移方程为 `dp[i][j] = dp[i-1][j] + dp[i][j-1]` 到达终点的路线数即为dp[m-1][n-1]

```java
class Solution {
    public int uniquePaths(int m, int n) {
        int[][] dp = new int[n][m];
        for(int i=0; i<n; i++){
            dp[i][0] = 1;
        }
        for(int j=1; j<m; j++){
            dp[0][j] = 1;
        }
        for(int i=1;i<n;i++){
            for(int j=1;j<m;j++){
                dp[i][j] = dp[i-1][j] + dp[i][j-1];
            }
        }
        return dp[n-1][m-1];
    }
}
```