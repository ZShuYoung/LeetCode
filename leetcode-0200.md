## 思路
- BFS
- 遍历每个点，如果是1，那么就做BFS处理，处理的逻辑如下，如果当前点是'1'，那么置为0，并且向上下左右BFS，这样就把某个'1'相邻的都置为了'0'。
- 每次遍历到1就表明是一个新的岛

```java
class Solution {
    public int numIslands(char[][] grid) {
        if(grid==null) return 0;
        int line = grid.length;
        if(line==0) return 0;
        int row = grid[0].length;
        if(row==0) return 0;

        int ans=0;
        for(int i=0; i<line; i++){
            for(int j=0; j<row; j++){
                if(grid[i][j]=='1'){
                    ans++;
                    bfs(i, j, grid);
                }
            }
        }
        return ans;
    }

    private void bfs(int i, int j, char[][] grid){
        if(i<0 || i>= grid.length || j<0 || j>= grid[0].length){
            return;
        }
        // 这里需要判断，因为BFS的时候不一定该位置上就是'1'
        if(grid[i][j]=='1'){
            grid[i][j]='0';
            bfs(i-1, j, grid);
            bfs(i+1, j, grid);
            bfs(i, j-1, grid);
            bfs(i, j+1, grid);
        }
    }
}
```