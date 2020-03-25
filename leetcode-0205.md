
```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        return helper(s, t) && helper(t, s);
    }

    private boolean helper(String s, String t){
        char[] hashMap = new char[256];
        char[] charS = s.toCharArray();
        char[] charT = t.toCharArray();
        for(int i=0; i<charS.length; i++){
            if(hashMap[charS[i] - ' '] == '\u0000'){
                hashMap[charS[i] - ' '] = charT[i];
            }else if(hashMap[charS[i] - ' '] != charT[i]){
                return false;
            }
        }
        return true;
    }
}
```