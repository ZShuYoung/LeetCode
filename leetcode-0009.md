## 思路
- 如果x为负，则肯定不是回文数
- x为正，拿翻转之后的与之比较

```java
class Solution {
    public boolean isPalindrome(int x) {
        if(x<0){
            return false;
        }
        return x==reverse(x);
    }

    private int reverse(int x){
        int ans=0;
        while(x>0){
            int tail = x%10;
            if(ans > Integer.MAX_VALUE/10 || (ans == Integer.MAX_VALUE/10 && tail > Integer.MAX_VALUE%10)){
                return -1;
            }
            ans = ans*10 + tail;
            x/=10;
        }
        return ans;
    }
}
```