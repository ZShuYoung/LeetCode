## 思路
- trim()过滤
- 对首字符做字母 '-' '+'校验
- 删除后面的字符
- 上述三步之后才是真正的string转int，需要注意正负最大整数的绝对值大小不一样

```java
class Solution {
    public int myAtoi(String str) {
        String temp = str.trim();
        if(temp.length()==0){
            return 0;
        }
        char c = temp.charAt(0);
        if(c<'0' && c>'9' && c!='-' && c!='+'){
            return 0;
        }
        boolean negative = false;
        if(c=='-'){
            negative = true;
        }
        if(c=='-' || c=='+'){
            temp=temp.substring(1);
            if(temp.length()==0){
                return 0;
            }
        }
        for(int i=0;i<temp.length();i++){
            char cc = temp.charAt(i);
            if(cc<'0' || cc>'9'){
                temp=temp.substring(0,i);
                break;
            }
        }
        if(temp.length()==0){
            return 0;
        }

        int ans=0;
        for(int i=0;i<temp.length();i++){
            int cur=temp.charAt(i)-'0';
            if(negative){
                if(ans > Integer.MAX_VALUE/10 || ( ans == Integer.MAX_VALUE/10 && cur > Integer.MAX_VALUE%10)){
                    return Integer.MIN_VALUE;
                }
            }else{
                if(ans > Integer.MAX_VALUE/10 || ( ans == Integer.MAX_VALUE/10 && cur >= Integer.MAX_VALUE%10)){
                    return Integer.MAX_VALUE;
                }
            }
            ans = ans*10 + cur;
        }
        return negative ? 0-ans : ans;
    }
}
```