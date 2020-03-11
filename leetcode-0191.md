## 思路
- 位运算，每次用一个1分别与0-31位上bit做与运算，不为0则表示有一个二进制1存在

```java
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int ans = 0;
        for(int i=0; i<32; i++){
            int mask = 1 << i;
            if((n & mask)!=0){
                ans++;
            }
        }
        return ans;
    }
}
```