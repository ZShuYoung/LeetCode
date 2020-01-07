## 思路
- 利用前面ThreeSum的思想
- 注意遍历的时候，对第一个数也要做去重

```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        List<List<Integer>> ans = new LinkedList<>();
        if (nums == null || nums.length < 4) {
            return ans;
        }
        Arrays.sort(nums);
        for (int i = 0; i < nums.length - 3; i++) {
            if (i == 0 || nums[i] != nums[i - 1]) {
                int newTarget = target - nums[i];
                List<List<Integer>> temp = threeSum(nums, newTarget, i + 1);
                if (temp.size() != 0) {
                    for (List<Integer> t : temp) {
                        List<Integer> oneAns = new LinkedList<>();
                        oneAns.add(nums[i]);
                        oneAns.addAll(t);
                        ans.add(oneAns);
                    }
                }
            }
        }
        return ans;
    }

    public List<List<Integer>> threeSum(int[] nums, int target, int index) {
        List<List<Integer>> ans = new LinkedList<>();
        if (nums == null || nums.length < 3) {
            return ans;
        }
        Arrays.sort(nums);
        for (int i = index; i < nums.length - 2; i++) {
            if (i == index || nums[i] != nums[i - 1]) {
                int j = i + 1, k = nums.length - 1;
                while (j < k) {
                    if (nums[i] + nums[j] + nums[k] == target) {
                        List<Integer> one = Arrays.asList(nums[i], nums[j], nums[k]);
                        ans.add(one);
                        while (j < k && nums[j] == nums[j + 1]) {
                            j++;
                        }
                        j++;
                    } else if (nums[i] + nums[j] + nums[k] < target) {
                        while (j < k && nums[j] == nums[j + 1]) {
                            j++;
                        }
                        j++;
                    } else {
                        while (j < k && nums[k] == nums[k - 1]) {
                            k--;
                        }
                        k--;
                    }
                }
            }
        }
        return ans;
    }
}
```