## 思路
- 动态规划
- 记dp[i]表示从1...i的数字可以有的BST数量，下面考虑状态转移方程
- 以{1,2,3,4}为例
```
以1为根节点的时候，{2,3,4}只能在右边，等同于{1,2,3}的数量
以2位根节点的时候，{1}在左边，{3,4}在右边
以3为根节点的时候，{1,2}在左边，{4}在右边
以4位根节点的时候，{1,2,3}在左边
```
- 最终状态转移方程式这样子 `dp[i] = dp[0]*dp[i-1] + dp[1]*dp[i-2] +...+ dp[i-1]*dp[0]` 其中dp[0]表示左子树或右子树为空，值为1

```java
class Solution {
    public int numTrees(int n) {
        // 因为dp[0]表示空左子树或右子树，所以要有n+1个
        int[] dp = new int[n+1];
        dp[0] = 1;
        dp[1] = 1;
        for(int i=2; i<=n; i++){
            // 这里total表示除去一个根节点之后剩下的数字个数，所以要减1
            int total = i-1;
            for(int left=0; left<=total; left++){
                dp[i] += dp[left]*dp[total-left];
            }
        }
        return dp[n];
    }
}
```

