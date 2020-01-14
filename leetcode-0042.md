## 思路
- 双指针法
- 从左侧起，找到第一个`height[l]>height[l+1]` 的点，因为只有这样才能形成凹槽；同理，从右侧起，找到第一个`height[r]>height[r-1]`的点
- 从这两点开始，根据高度计算，并最终合并
```
// 只要l后面的高度还比l低，就可以形成凹槽
while(l<r && leftHeight>=height[++l]){
    ans += leftHeight - height[l];
}
```

```java
class Solution {
    public int trap(int[] height) {
        int l=0, r=height.length-1;
        int ans=0;
        while(l<r && height[l]<=height[l+1]){
            l++;
        }
        while(l<r && height[r]<=height[r-1]){
            r--;
        }
        while(l<r){
            int leftHeight=height[l];
            int rightHeight=height[r];
            if(leftHeight<rightHeight){
                while(l<r && leftHeight>=height[++l]){
                    ans += leftHeight - height[l];
                }
            }else{
                while(l<r && rightHeight>=height[--r]){
                    ans += rightHeight - height[r];
                }
            }
        }
        return ans;
    }
}
```