## 基本思路
- 时间换空间，一次遍历，通过map查询速度为O(1)的特性快速找到另一个加数
  
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>(nums.length);
        for(int index=0; index<nums.length; index++){
            int another = target - nums[index];
            if(map.containsKey(another)){
                return new int[]{map.get(another), index};
            }else{
                map.put(nums[index], index);
            }
        }
        return new int[]{-1,-1};
    }
}
```