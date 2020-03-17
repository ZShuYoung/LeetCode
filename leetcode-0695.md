## 思路
- 遍历整个二维数组，当出现1，说明出现海岛，从该点开始bfs/dfs
- 

```java
class Solution {
    private int temp=0;

    public int maxAreaOfIsland(int[][] grid) {
        if(grid==null || grid.length==0 || grid[0].length==0) return 0;
        int ans=0;
        for(int i=0; i<grid.length; i++){
            for(int j=0; j<grid[0].length; j++){
                if(grid[i][j]==1){
                    temp=0;
                    bfs(i, j, grid);
                    ans = Math.max(ans, temp);
                }
            }
        }
        return ans;
    }

    private void bfs(int i, int j, int[][] grid){
        if(i<0 || i>=grid.length || j<0 || j>=grid[0].length) return;
        if(grid[i][j]==1){
            this.temp++;
            grid[i][j]=0;
            bfs(i-1,j,grid);
            bfs(i+1,j,grid);
            bfs(i,j-1,grid);
            bfs(i,j+1,grid);
        }
    }
}
```