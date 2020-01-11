## 思路
- 二分查找：不管转折点在哪里，[start,mid]和[mid,end]至少有半边是顺序的
- 如果左侧是顺序的并且target在其中，则抛弃右侧，否则抛弃左侧
- 如果右侧是顺序的，同理

```java
class Solution {
    public int search(int[] nums, int target) {
        int start=0,end=nums.length-1;
        int mid;
        while(start<=end){
            mid=(start+end)/2;
            if(nums[mid]==target){
                return mid;
            }
            // 左半部分有序
            if(nums[start]<=nums[mid]){
                if(nums[start]<=target && target<nums[mid]){
                    end=mid-1;
                }else{
                    start=mid+1;
                }
            }else{
                if(nums[mid]<target && target<=nums[end]){
                    start=mid+1;
                }else{
                    end=mid-1;
                }
            }
        }
        return -1;
    }
}
```