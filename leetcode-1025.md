## 思路

记dp[i]表示数字为i的时候爱丽丝是否可以赢，那么就有以下状态转移方程：
`dp[i] = true (0<x<i && dp[i-x]==false)`

```java
class Solution {
    // 递归
    public boolean divisorGame2(int n) {
        if(n==1) return false;
        for(int i=1; i<n; i++){
            if(n % i==0 && divisorGame(n-i)==false){
                return true;
            }
        }
        return false;
    }

    // 动态规划
    public boolean divisorGame(int n) {
        boolean[] dp = new boolean[n+1];
        dp[1] = false;
        for(int i=2; i<=n; i++){
            for(int x=1; x<i; x++){
                if(i % x==0 && dp[i-x]==false){
                    dp[i]=true;
                    break;
                }
            }
        }
        return dp[n];
    }
}
```