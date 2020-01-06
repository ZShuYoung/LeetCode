## 思路
- 其实和leetcode15一样，主要过滤重复数字即可

```java
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);
        int diff=Integer.MAX_VALUE;
        int res=0;
        for(int i=0;i<nums.length-2;i++){
            if(i==0 || nums[i]!=nums[i-1]){
                int left=i+1,right=nums.length-1;
                while(left<right){
                    if(nums[i]+nums[left]+nums[right]==target){
                        return target;
                    }else if(nums[i]+nums[left]+nums[right] < target){
                        if(Math.abs(nums[i]+nums[left]+nums[right]- target) < diff){
                            diff=Math.abs(nums[i]+nums[left]+nums[right]- target);
                            res= nums[i]+nums[left]+nums[right];
                        }
                        while(left<right && nums[left]==nums[left+1]){
                            left++;
                        }
                        left++;
                    }else{
                        if(Math.abs(nums[i]+nums[left]+nums[right]- target) < diff){
                            diff=Math.abs(nums[i]+nums[left]+nums[right]- target);
                            res= nums[i]+nums[left]+nums[right];
                        }
                        while(left<right && nums[right]==nums[right-1]){
                            right--;
                        }
                        right--;
                    }
                }
            }
        }
        return res;
    }
}
```