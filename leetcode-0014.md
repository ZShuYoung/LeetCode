## 思路
- 以第一个string做样本，对位置的字符，拿其他string在同位置做比较
- 如果后续有出现任何一个string长度不够或者相同index处字符不一致则终止

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs==null || strs.length==0){
            return "";
        }
        StringBuilder sb = new StringBuilder();
        String first = strs[0];
        for(int i=0;i<first.length();i++){
            char c = first.charAt(i);
            for(int index=1;index<strs.length;index++){
                if(strs[index].length()<i+1 || strs[index].charAt(i)!=c){
                    return sb.toString();
                }
            }
            sb.append(c);
        }
        return sb.toString();
    }
}
```