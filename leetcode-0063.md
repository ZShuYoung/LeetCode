## 思路
- 动态规划
- 状态转移方程其实还是 `dp[i][j] = dp[i-1][j] + dp[i][j-1]` 但是前提条件 `obstacleGrid[i][j] != 1 (不为障碍)`， 否则`dp[i][j] = 0`

```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        if(obstacleGrid[0][0]==1){
            return 0;
        }
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        int[][] dp = new int[m][n];
        dp[0][0] = 1;
        for(int i=1;i<m;i++){
            if(dp[i-1][0]==1 && obstacleGrid[i][0]==0){
                dp[i][0] = 1;
            }else{
                dp[i][0] = 0;
            }
        }
        for(int j=1;j<n;j++){
            if(dp[0][j-1]==1 && obstacleGrid[0][j]==0){
                dp[0][j] = 1;
            }else{
                dp[0][j] = 0;
            }
        }
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                if(obstacleGrid[i][j]==0){
                    dp[i][j] = dp[i-1][j] + dp[i][j-1];
                }else{
                    dp[i][j] = 0;
                }
            }
        }
        return dp[m-1][n-1];
    }
}
```