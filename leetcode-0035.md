## 思路
- 二分查找
- 前面的逻辑和普通的二分查找没有区别，关键在于循环结束后怎么判断。最后一次循环肯定是start==mid==end，然后执行了一次判断后退出循环
- 如果最后一次 `nums[mid]<target` ，那么start+1了，这个时候target就应该处在target+1 的位置
- 如果最后一次 `nums[mid]>target` ，那么end-1了，这个时候target就应该处在mid 的位置

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int start=0, end=nums.length-1;
        int mid=0;
        while(start<=end){
            mid=(start+end)/2;
            if(nums[mid]==target){
                return mid;
            }else if(nums[mid]<target){
                start=mid+1;
            }else{
                end=mid-1;
            }
        }
        if(nums[mid]<target){
            return start;
        }
        return mid;
    }
}
```