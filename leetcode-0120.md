## 思路
- 动态规划，从底往上

```java
class Solution {
    public int minimumTotal(List<List<Integer>> triangle) {
        // dp[i][j]表示从[i,j]到顶点[0,0]的最短距离
        // 为什么从下往上：因为如果从上往下，那么还要判断最后一层dp[triangle.size()-1]中的最小元素
        int row = triangle.size();
        int column = triangle.get(row-1).size();
        int[][] dp = new int[row][column];
        for(int j=0; j<column; j++){
            dp[row-1][j] = triangle.get(row-1).get(j);
        }
        for(int i=row-2; i>=0; i--){
            for(int j=0; j<=i; j++){
                dp[i][j] = triangle.get(i).get(j) + Math.min(dp[i+1][j], dp[i+1][j+1]);
            }
        }
        return dp[0][0];
    }
}
```