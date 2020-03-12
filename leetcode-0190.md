

```java
public class Solution {
    // you need treat n as an unsigned value
    public int reverseBits(int n) {
        int ans = 0;
        for(int i=0; i<32; i++){
            int mask = 1 << i;
            if((n & mask) !=0){
                int reverseMask = 31 - i;
                ans += (1 << reverseMask);
            }
        }
        return ans;
    }
}
```
