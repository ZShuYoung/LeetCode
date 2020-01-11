## 思路
- 二分查找
- 相比于在一个数组中找到其中一个，这次找左右的范围，那么和二分查找不一样的就是找到`nums[mid]==target` 时的处理；当存在target的时候，要找左边间，那么不然是`end=mid-1` 从[start, mid-1]区间内再找可以存在的target
- 右侧同理

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int left = findLeft(nums,target);
        int right = findRight(nums,target);
        return new int[]{left,right};
    }

    private int findLeft(int[] nums, int target) {
        int start=0, end=nums.length-1;
        int mid=0;
        int index=-1;
        while(start<=end){
            mid=(start+end)/2;
            if(nums[mid]==target){
                index=mid;
                end=mid-1;
            }else if(nums[mid]<target){
                start=mid+1;
            }else{
                end=mid-1;
            }
        }
        return index;
    }

    private int findRight(int[] nums, int target) {
        int start=0, end=nums.length-1;
        int mid=0;
        int index=-1;
        while(start<=end){
            mid=(start+end)/2;
            if(nums[mid]==target){
                index=mid;
                start=mid+1;
            }else if(nums[mid]<target){
                start=mid+1;
            }else{
                end=mid-1;
            }
        }
        return index;
    }
}
```