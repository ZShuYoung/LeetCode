## 思路
- 一次遍历，用minPrice记录遍历过程中最小的价格，用ans记录遍历过程中的最大收益
- 遍历到索引i的时候，如果`price[i]>minPrice`，那么拿已缓存的ans和price[i]-minPrice比较，更新最大收益，为什么要比较。考虑[1,5,2]这种场景
- 如果`price[i]<=minPrice`，那么更新minPrice，表明当前点肯定不能卖出，最大收益还是之前缓存的ans

```java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices==null || prices.length<2) return 0;
        int minPrice = prices[0];
        int ans = Integer.MIN_VALUE;
        for(int i=1; i<prices.length; i++){
            if(prices[i]>minPrice){
                ans = Math.max(prices[i]-minPrice, ans);
            }else{
                minPrice = prices[i];
            }
        }
        return ans==Integer.MIN_VALUE ? 0 : ans;
    }
}
```