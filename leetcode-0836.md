## 思路
- 先找出靠左的矩形，如果靠左的右边在右侧矩形的左边，那必不可能相交
- 再找出下边的矩形，如果下边的上边在上侧矩形的下边，那也必不可能相交

```java
class Solution {
    public boolean isRectangleOverlap(int[] rec1, int[] rec2) {
        if(rec1[0]<rec2[0]){
            return helper(rec1, rec2);
        }
        return helper(rec2, rec1);
    }

    private boolean helper(int[] left, int[] right){
        if(left[2] <= right[0]) return false;
        if(left[1] < right[1]){
            return helper2(left, right);
        }
        return helper2(right, left);
    }

    private boolean helper2(int[] low, int[] high){
        if(low[3] <= high[1]) return false;
        return true;
    }
}
```