## 思路
- 双指针，注意字符和数字的判断方法

```java
class Solution {
    public boolean isPalindrome(String s) {
        char[] strChar = s.toLowerCase().toCharArray();
        int start=0, end=strChar.length-1;
        while(start<end){
            if(!(strChar[start]>='a' && strChar[start]<='z') && !(strChar[start]>='0' && strChar[start]<='9')){
                start++;
                continue;
            }
            if(!(strChar[end]>='a' && strChar[end]<='z') && !(strChar[end]>='0' && strChar[end]<='9')){
                end--;
                continue;
            }
            if(strChar[start]!=strChar[end]){
                return false;
            }else{
                start++;
                end--;
            }
        }
        return true;
    }
}
```