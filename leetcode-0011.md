## 思路
- 如果以纵轴为左边，横轴为右边，题目的本质就是在二维数组的上半区的点中找到一个值最大的点

```
  1 2 3 4 5 6
1 x 
2 x x
3 x x x 
4 x x x x
5 x x x x x
6 x x x x x x
```

- 暴力方法是逐个遍历
- 以[1,6]为例，如果`height[1]<height[6]`，那么基于最短板原则，[1,2]~[1,5]均可以跳过

```
  1 2 3 4 5 6
1 x - - - - o
2 x x
3 x x x 
4 x x x x
5 x x x x x
6 x x x x x x
```

- 根据上面的条件，循环的重点是left==right，每到一个点都要缓存最大存水量

```java
class Solution {
    public int maxArea(int[] height) {
        int max=0;
        int left=0, right=height.length-1;
        int leftHeight, rightHeight;
        while(left<right){
            leftHeight=height[left];
            rightHeight=height[right];
            max = Math.max(max, (right-left)*Math.min(leftHeight,rightHeight));

            if(leftHeight<rightHeight){
                left++;
            }else{
                right--;
            }
        }
        return max;
    }
}
```