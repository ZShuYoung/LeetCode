## 思路
- 动态规划
- dp[i]表示字符串到第i个位置所有的可能编码个数
- 对于dp[i+1]. 如果s[i+1]的数字在1-9，那么dp[i+1]和dp[i]编码个数一样
- 如果s[i]和s[i+1]的数字在10~26，那么dp[i+1]还能再加上dp[i-1]

```java
class Solution {
    public int numDecodings(String s) {
        if(s.startsWith("0")) return 0;
        int[] dp = new int[s.length()+1];   // 这里dp数组长度并不是和s长度一样
        dp[0] = 1;  // 这里是个trick
        dp[1] = 1;
        for(int i=2; i<dp.length; i++){
            int index = i-1;
            int cur = Integer.parseInt(s.substring(index,index+1));
            int pre = Integer.parseInt(s.substring(index-1,index+1));
            if(cur>=1 && cur<=9){
                dp[i] += dp[i-1];
            }
            if(pre>=10 && pre<=26){
                dp[i] += dp[i-2];
            }
        }
        return dp[s.length()];
    }
}
```