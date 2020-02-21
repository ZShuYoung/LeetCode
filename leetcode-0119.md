## 思路
- 递归，同#118

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> ans = new LinkedList<>();
        if(rowIndex==0){
            ans.add(1);
            return ans;
        }
        if(rowIndex==1){
            ans.add(1);
            ans.add(1);
            return ans;
        }
        List<Integer> pre = getRow(rowIndex-1);
        List<Integer> next = new LinkedList<>();
        next.add(1);
        for(int i=0; i<pre.size()-1; i++){
            int sum = pre.get(i) + pre.get(i+1);
            next.add(sum);
        }
        next.add(1);
        return next;
    }
}
```