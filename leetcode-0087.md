## 思路
- 既然要保存在数组里面nums1，并且nums1和nums2都是有序的，那么就从数组后排开始遍历，大的数字塞在nums1的后面

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int index = m+n-1;
        while(index>=0){
            int number1 = m>=1 ? nums1[m-1] : Integer.MIN_VALUE;
            int number2 = n>=1 ? nums2[n-1] : Integer.MIN_VALUE;
            if(number1 < number2){
                nums1[index--] = number2;
                n--;
            }else{
                nums1[index--] = number1;
                m--;
            }
        }
    }
}
```