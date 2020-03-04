## 思路
- 因为题目给出 `nums[-1] = nums[n] = -∞` ，那么沿着 `nums[m] > nums[m+1] 必能找到一个m，该位置处于一个峰值`

```java
class Solution {
    public int findPeakElement(int[] nums) {
        int left=0, right=nums.length-1;
        int mid;
        while(left < right){
            mid = (left + right)/2;
            if(nums[mid]>nums[mid+1]){
                right=mid;
            }else{
                left=mid+1;
            }
        }
        return left;
    }
}
```