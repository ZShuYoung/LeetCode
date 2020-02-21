## 思路
- 递归
- 先求numRows-1的值，取最后一行假设为[1,i,i+1,i+2...1]
- 那么下一行的前后分别是1，中间分别为上一行的相邻两数之和

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> ans = new LinkedList<>();
        if(numRows==0) return ans;
        if(numRows==1){
            List<Integer> levelOne = new LinkedList<>();
            levelOne.add(1);
            ans.add(levelOne);
            return ans;
        }
        if(numRows==1){
            List<Integer> levelOne = new LinkedList<>();
            levelOne.add(1);
            List<Integer> levelTwo = new LinkedList<>();
            levelTwo.add(1);
            levelTwo.add(1);
            ans.add(levelOne);
            ans.add(levelTwo);
            return ans;
        }
        List<List<Integer>> pre = generate(numRows-1);
        List<Integer> preLevel = pre.get(pre.size()-1);
        List<Integer> nextLevel = new LinkedList<>();
        nextLevel.add(1);
        for(int i=0; i<preLevel.size()-1; i++){
            int sum = preLevel.get(i) + preLevel.get(i+1);
            nextLevel.add(sum);
        }
        nextLevel.add(1);
        pre.add(nextLevel);
        return pre;
    }
}
```