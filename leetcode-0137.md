## 思路
- 还是位运算，如果把数字转成二进制，因为只有一个数字没有出现三次，那么如果所有位的数字相加，每位上结果不为3的倍数的位组成的数字即为那个没有出现三次的数字
- 以[4,4,4,7,7,7,6]为例，这里只展示低8位，前面24位全是0就不展示了

```
4        0000 0100
4        0000 0100
4        0000 0100
7        0000 0111
7        0000 0111
7        0000 0111
6        0000 0110
sum      0000 0743
每位对3去膜之后就成了  0000 0110正好对于只出现了一次的6
```

```java
class Solution {
    public int singleNumber(int[] nums) {
        int ans = 0;
        for(int i=0; i<32; i++){
            int mask = 1<<i;
            int tempSum = 0;
            for(int n : nums){
                if((n & mask) != 0){
                    tempSum++;
                }
            }
            if(tempSum % 3 !=0){
                ans |= mask;
            }
        }
        return ans;
    }
}
```