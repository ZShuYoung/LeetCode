## 思路
- 需要考虑整数溢出的问题
- 这里讨巧使用long类型，对溢出场景做了判断

```java
class Solution {
    public int reverse(int x) {
        long res = 0;
        while(x!=0){
            int tail = x%10;
            if(res*10 > Integer.MAX_VALUE || (res*10 == Integer.MAX_VALUE && tail> Integer.MAX_VALUE%10)){
                return 0;
            }
            if(res*10 < Integer.MIN_VALUE || (res*10 == Integer.MAX_VALUE && tail< Integer.MIN_VALUE%10)){
                return 0;
            }
            res = res*10 + tail;
            x/=10;
        }
        return (int)res;
    }
}
```