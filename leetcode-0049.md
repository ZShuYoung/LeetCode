## 思路
- 将string转成char[] 再用Arrays.sort()进行排序之后再转成string，这样就对每个string做了字典序重拍
- 用一个Map<String, Integer>缓存已经遍历过的string，key为字典序重拍之后的string，value是结果list的index

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> ans = new LinkedList<>();
        Map<String, Integer> map = new HashMap<>();
        for(String s : strs){
            char[] chars = s.toCharArray();
            Arrays.sort(chars);
            String temp = String.valueOf(chars);
            if(map.containsKey(temp)){
                int index = map.get(temp);
                List<String> cur = ans.remove(index);
                cur.add(s);
                ans.add(index, cur);
            }else{
                map.put(temp, ans.size());
                List<String> one = new LinkedList<>();
                one.add(s);
                ans.add(one);
            }
        }
        return ans;
    }
}
```