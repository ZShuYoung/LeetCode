## 思路
- 和#35题思路一样，在判断半边是否为顺序的时候需要考虑`[3,1,2,3,3,3,3]`这种情况，不能仅仅根据`nums[start]<=nums[mid]` 就认为左半边是顺序的，要单独判断`nums[start]==nums[mid]`的场景

```java
class Solution {
    public boolean search(int[] nums, int target) {
        int start=0, end=nums.length-1;
        int mid;
        while(start<=end){
            mid = (start+end)/2;
            if(nums[mid]==target){
                return true;
            }
            if(nums[start]<nums[mid]){ // 35题这里是nums[start]<=nums[mid],因为不存在相同的数
                if(nums[start]<=target && target<nums[mid]){
                    end = mid-1;
                }else{
                    start = mid+1;
                }
            }else if(nums[start]==nums[mid]){ // 这里有区别
                start++;
            }else{
                if(nums[mid]<target && target<=nums[end]){
                    start = mid+1;
                }else{
                    end = mid-1;
                }
            }
        }
        return false;
    }
}
```