## 思路
- 这是一道找规律的题目，发现规律之后其实很简单
- n=0 返回[0] 这是起始条件
- n=1 1位格雷码，那么可能是0或者1，对应返回可以是[0,1]或[1,0]，这里以[0,1]为例
- n=2的时候，因为码数变多了，所以最直接的就是在1的基础上在前面加0或者1
```
 n=1      n=2        n=2

 0        00         00
 1        01         01
          10         11
          11         10
```
- 这里[00,01,10,11]是不满足格雷码要求的，但是如果把下面的一半翻转一下变成[00,01,11,10]就满足了
- 上半部分的值不变，下半部分拿上半部分的翻转再左移1的i位就行了

```java
class Solution {
    public List<Integer> grayCode(int n) {
        List<Integer> ans = new LinkedList<>();
        ans.add(0);
        for(int i=0; i<n; i++){
            int add = 1 << i;
            for(int j=ans.size()-1; j>=0; j--){
                ans.add(ans.get(j) + add);
            }
        }
        return ans;
    }
}
```