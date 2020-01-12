## 思路
- 由于n要基于上一次的值来产生，所以思路是递归
- 递归终止条件n==1的时候返回 `"1"`
- 遍历n-1的返回，用一个pre记录上一次遍历的字符，用count记录个数；当当前字符与pre相同时，count加一；否则可以把上一个字符和个数输出
- 注意最后输出的时候要带上pre和count

```java
class Solution {
    public String countAndSay(int n) {
        if(n==1){
            return "1";
        }
        StringBuilder ans = new StringBuilder();
        String str = countAndSay(n-1);
        char pre = '#';
        int count = 0;
        for(int i=0;i<str.length();i++){
            char current = str.charAt(i);
            if(pre=='#'){
                pre = current;
                count++;
            }else if(current == pre){
                count++;
            }else{
                ans.append(count).append(pre);
                pre=current;
                count=1;
            }
        }
        return ans.append(count).append(pre).toString();
    }
}
```