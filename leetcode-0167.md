## 思路
- 因为是排序的，所以双指针一前一后，后面的往前；小就前面的往后

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left=0, right=numbers.length-1;
        while(true){
            if(numbers[left] + numbers[right] < target){
                left++;
            }else if(numbers[left] + numbers[right] > target){
                right--;
            }else{
                break;
            }
        }
        return new int[]{left+1, right+1};
    }
}
```