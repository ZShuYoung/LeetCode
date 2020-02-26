## 思路
- 回溯算法
- 基本思路是每次每一段都从小到大取，以"abba"为例。for循环实际上是指从index开始，截取不断边长的一段，判断其为回文串后，再继续起后面的一段判断怎么拆成回文串

```java
class Solution {
    public List<List<String>> partition(String s) {
        List<List<String>> ans = new LinkedList<>();
        List<String> one = new LinkedList<>();
        backTrack(ans, one, s, 0);
        return ans;
    }

    private void backTrack(List<List<String>> ans, List<String> one, String s, int index){
        if(index==s.length()){
            ans.add(new LinkedList<String>(one));
            return;
        }
        for(int i=1; i<=s.length()-index; i++){
            String temp = s.substring(index, index+i);
            if(helper(temp)){
                one.add(temp);
                // 这里从temp的右边界开始
                backTrack(ans, one, s, index+i);
                one.remove(one.size()-1);
            }
        }
    }

    private boolean helper(String temp){
        int start=0, end=temp.length()-1;
        while(start<end){
            if(temp.charAt(start) != temp.charAt(end)){
                return false;
            }
            start++;
            end--;
        }
        return true;
    }
}
```