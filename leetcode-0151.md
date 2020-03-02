## 思路
- 简单题

```java
class Solution {
    public String reverseWords(String s) {
        String[] strs = s.split(" ");
        StringBuilder ans = new StringBuilder();
        for(int i=strs.length-1; i>=0; i--){
            if(strs[i].length()!=0){
                ans.append(strs[i]).append(" ");
            }
        }
        return ans.toString().trim();
    }
}
```