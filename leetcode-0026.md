## 思路
- 使用一个index记录不重复的nums下标，那么令index从0开始
- 从i=1开始遍历数组，如果num[i]与nums[index]不等，则nums[index+1]的位置应该是nums[i]，且index+1

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int index=0;
        for(int i=1;i<nums.length;i++){
            if(nums[i]!=nums[index]){
                nums[++index]=nums[i];
            }
        }
        return index+1;
    }
}
```