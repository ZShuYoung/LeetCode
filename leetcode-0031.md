## 思路
- 以 `[2,3,4,8,9,5]` 为例
- 首先找到最大的位置k,满足 `nums[k]<nums[k+1]` ,如果找不到，那么说明原来的数组是倒序的，类似于 `[9,8,5,4,3,2]` 这种，所以就直接翻转数组即可
- 如果存在满足 `nums[k]<nums[k+1]` 的最大数k，那么从 `nums[k+1,end]` 这段必然是倒序的，所以从末尾处找一个最大下标l，使其满足 `nums[k]<nums[l]`
- 交换k和l的位置得到 `[2,3,4,8,9,5]`
- 将`nums[k+1,end]` 这部分翻转

```java
class Solution {
    public void nextPermutation(int[] nums) {
        int k=0,l=0;
        for(k=nums.length-2;k>=0;k--){
            if(nums[k]<nums[k+1]){
                break;
            }
        }
        if(k==-1){
            reverse(nums,0,nums.length-1);
            return;
        }

        for(l=nums.length-1;l>k;l--){
            if(nums[l]>nums[k]){
                swap(nums,k,l);
                reverse(nums,k+1,nums.length-1);
                return;
            }
        }
    }

    private void swap(int[] n, int start, int end){
        int temp = n[start];
        n[start] = n[end];
        n[end] = temp;
    }

    private void reverse(int[] n, int start, int end){
        while(start<end){
            swap(n,start,end);
            start++;
            end--;
        }
    }
}
```