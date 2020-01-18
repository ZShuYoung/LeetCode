## 思路
- 使用四个变量记录矩阵的四边，left buttom left right
- 循环的条件就是 `top <= buttom && left <= right`
- 循环里面因为四边会汇聚，所以要加上判断

```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        if(matrix==null || matrix.length==0){
            return new ArrayList<Integer>();
        }
        int top=0, buttom=matrix.length-1, left=0, right=matrix[0].length-1;
        List<Integer> ans = new ArrayList<>();
        while(top <= buttom && left<=right){
            for(int i=left; i<=right; i++){
                ans.add(matrix[top][i]);
            }
            top++;

            for(int j=top; j<= buttom; j++){
                ans.add(matrix[j][right]);
            }
            right--;

            if(top<=buttom){
                for(int i=right; i>=left; i--){
                    ans.add(matrix[buttom][i]);
                }
                buttom--;
            }

            if(left<=right){
                for(int j=buttom; j>=top; j--){
                    ans.add(matrix[j][left]);
                }
                left++;
            }
        }
        return ans;
    }
}
```