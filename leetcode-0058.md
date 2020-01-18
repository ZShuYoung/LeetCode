## 思路
- 和56题的思路一样，用四个变量记录四条边界
- 循环条件是 `top <= buttom && left <= right`

```java
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] ans = new int[n][];
        for(int i=0; i<n; i++){
            int[] temp = new int[n];
            ans[i] = temp;
        }
        int top=0, buttom=n-1, left=0, right=n-1;
        int index=1;
        while(top<=buttom && left<=right){
            for(int i=left; i<=right; i++){
                ans[top][i] = index++;
            }
            top++;

            for(int j=top; j<=buttom; j++){
                ans[j][right] = index++;
            }
            right--;

            if(top<=right){
                for(int i=right; i>=left; i--){
                    ans[buttom][i] = index++;
                }
                buttom--;
            }

            if(left<=right){
                for(int j=buttom; j>=top; j--){
                    ans[j][left] = index++;
                }
                left++;
            }
        }
        return ans;
    }
}
```