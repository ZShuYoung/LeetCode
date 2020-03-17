## 思路
- 因为单词只包含26个小写字母，所以维持一个以为数字，每一位记录对应字母的个数，然后遍历每个单词的每个字母，出现一个就减1
- 每次遍历完则说明可以找到，就加上该单词的长度

```java
class Solution {
    public int countCharacters(String[] words, String chars) {
        int[] number = new int[26];
        char[] charsArray = chars.toCharArray();
        for(char c : charsArray){
            number[c - 'a']++;
        }

        int ans = 0;
        for(String word : words){
            int same = 0;
            int[] temp = Arrays.copyOf(number, number.length);
            for(char c : word.toCharArray()){
                if(temp[c - 'a']>0){
                    temp[c - 'a']--;
                    same++;
                }
            }
            if(same==word.length()){
                ans+=same;
            }
        }
        return ans;
    }
}
```