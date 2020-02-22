## 思路
- 贪心算法
- 一次遍历数组，涨价就买；跌价就不卖

```java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices==null || prices.length<2) return 0;
        int ans = 0;
        for(int i=0; i<prices.length-1; i++){
            int j=i+1;
            if(prices[j]>prices[i]){
                ans += prices[j] - prices[i];
            }
        }
        return ans;
    }
}
```