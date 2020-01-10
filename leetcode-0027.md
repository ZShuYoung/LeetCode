## 思路
- 使用一个index记录不重复的nums下标，那么令index从0开始
- 从i=0开始遍历数组，如果num[i]与nums[index]不等，则nums[index+1]的位置应该是nums[i]，且index+1
- 注意下循环中index已++，所以return的时候不需要再+1了

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int index=0;
        for(int i=0;i<nums.length;i++){
            if(nums[i]!=val){
                nums[index++]=nums[i];
            }
        }
        return index;
    }
}
```