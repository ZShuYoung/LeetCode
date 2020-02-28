## 思路
- 一个数与自己做亦或运算得0
- 一个数与0做亦或运算还是自身

```java
class Solution {
    public int singleNumber(int[] nums) {
        int ans = 0;
        for(int num : nums){
            ans ^= num;
        }
        return ans;
    }
}
```