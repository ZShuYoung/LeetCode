## 思路
- 先排序
- `所有满足条件且不重复的三元组` 所以要过滤
- 对排序后的数组，从头开始遍历，再配合双指针滑动

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        for(int i=0;i<nums.length-2;i++){
            if(nums[i] > 0){
                break;
            }
            if(i>=1 && nums[i]==nums[i-1]){
                continue;
            }
            int left=i+1, right=nums.length-1;
            int target = 0-nums[i];
            while(left<right){
                if(nums[left]+nums[right] == target){
                    List<Integer> one = Arrays.asList(nums[i], nums[left], nums[right]);
                    res.add(one);
                    while(left+1<right && nums[left]==nums[left+1]){
                        left++;
                    }
                    left++;
                    while(left<right-1 && nums[right]==nums[right-1]){
                        right--;
                    }
                    right--;
                }else if(nums[left]+nums[right] < target){
                    while(left+1<right && nums[left]==nums[left+1]){
                        left++;
                    }
                    left++;
                }else{
                    while(left<right-1 && nums[right]==nums[right-1]){
                        right--;
                    }
                    right--;
                }
            }
        }
        return res;
    }
}
```