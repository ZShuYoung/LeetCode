## 思路
- 和 `删除排序数组中的重复项` 很想，要用一个index变量指示删除重复项之后的数组下标
- 因为是排过序了，用`pre`记录前一个位置的数字；用`count`记录`pre`的值已经出现过几次
- 初始情况为 pre = nums[0]    count = 1   index = 1
- 那么从1开始遍历整个数组。如果nums[i]!=pre 那么index的位置肯定就放nums[i]；如果nums[i]==pre，就判断count的值，如果是1，那么index的位置还可以放nums[i]，并且count增加为2，否则nums[i]就是应该被删除的重复项

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums==null) return 0;
        if(nums.length <= 2) return nums.length;
        int pre = nums[0];
        int count = 1;
        int index = 1;
        for(int i=1; i<nums.length; i++){
            if(nums[i]!=pre){
                pre=nums[i];
                count=1;
                nums[index++]=nums[i];
            }else{
                if(count==1){
                    count=2;
                    nums[index++]=nums[i];
                }else{
                    // 删掉该项
                    continue;
                }
            }
        }
        return index;
    }
}
```