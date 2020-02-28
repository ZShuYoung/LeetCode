## 思路
- 加油站问题分两个步骤去处理
- 如果总的油量 >= 总的消耗量，必然有解，所以先判断是否有解
- 有解的话，用贪心的算法找到起点位置

```java
class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int total = 0;
        for(int i=0; i<gas.length; i++){
            total += gas[i] - cost[i];
        }
        if(total < 0) return -1;

        int start = 0;
        total = 0;
        for(int i=0; i<gas.length; i++){
            total += gas[i] - cost[i];
            if(total < 0){
                start = i+1;
                total=0;
            }
        }
        return start;
    }
}
```