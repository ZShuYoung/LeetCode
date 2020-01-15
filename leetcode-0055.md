## 思路
- 贪心算法
- 用一个fastest变量记录每走到一个点为止所能够到的最远距离，那么fastest=0表示最开始只能在第一个点，destination记录最后一个点的下标
- 从第一个点开始，每到一个点，先将fastest与destination比较，大则说明能达到终点；否则就先判断能否到达当前点`fastest>=i` ,不能则直接结束；可以则更新fastest
- 循环到前一个点为止，在循环结束后最后判断一下fastest和destination的大小

```java
class Solution {
    public boolean canJump(int[] nums) {
        int fastest=0;
        int destination = nums.length-1;
        for(int i=0;i<nums.length-1;i++){
            if(fastest>=destination){
                return true;
            }
            if(fastest<i){
                return false;
            }
            fastest = Math.max(fastest, i+nums[i]);
        }
        return fastest>=nums.length-1;
    }
}
```