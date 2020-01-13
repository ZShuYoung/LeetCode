## 思路
- 其实就是两次翻转
- 第一次沿中间上下翻转
- 第二次沿左上到右下对角线翻转

```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        // 先上下半边翻转
        for(int i=0; i<n/2;i++){
            int[] temp = matrix[i];
            matrix[i] = matrix[n-1-i];
            matrix[n-1-i] = temp;
        }

        // 沿左上到右下对角处对折
        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
    }
}
```