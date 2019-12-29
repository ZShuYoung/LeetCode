## 基本思路

1. 以滑动窗口法来思考最长无重复字符子串的问题
2. 窗口右侧往右滑，直到字符串末端；使用一个map缓存已有字符和对应的位置
   - 每滑动一次结束后，讲当前窗口长度与缓存的最大长度做比较
   - 如果新滑进来的字符不包含在老窗口的字符内，则把新字符加入map中
   - 如果新的字符已存在，那么则需要把窗口的左侧挪到老字符的后一位

`left = Math.max(left, map.get(newChar)+1);`
这里需要注意一下，如果只写出`left = map.get(newChar)+1;` 那么对于`abba`这种情况就出错了，因为每次滑动并没有重置map;重置map会消耗更多时间

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int max=0;
        Map<Character, Integer> map = new HashMap<>();
        for(int left=0,right=0;right<s.length();right++){
            char newChar = s.charAt(right);
            if(map.containsKey(newChar)){
                left = Math.max(left, map.get(newChar)+1);
                map.put(newChar, right);
            }else{
                map.put(newChar, right);
            }
            max = Math.max(max, right-left+1);
        }
        return max;
    }
}
```