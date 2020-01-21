## 思路
- 考虑到矩阵特点，从左下角（或者右上角）开始探索
- 小于target则往右挪
- 大于target则往上挪
- 如果挪出矩阵边界了 那就说明不存在

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row = matrix.length-1;
        int column = 0;
        while(row>=0 && column< matrix[0].length){
            if(matrix[row][column] == target){
                return true;
            }else if(matrix[row][column] < target){
                column++;
            }else{
                row--;
            }
        }
        return false;
    }
}
```