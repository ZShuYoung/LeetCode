## 思路
- dfs bfs
- 从四周的每个点，如果点是O那么向周围遍历，并重写为*，*代表不是被围绕的点
- 四周dfs之后所有不是周围的点都被改成了*，被包围的点还是O，所以再遍历一次把O改成X，把*改成O

```java
class Solution {
    public void solve(char[][] board) {
        if(board.length<3 || board[0].length<3) return;
        for(int i=0; i<board.length; i++){
            dfs(i, 0, board);
            dfs(i, board[0].length-1, board);
        }
        for(int j=0; j<board[0].length; j++){
            dfs(0, j, board);
            dfs(board.length-1, j, board);
        }

        for(int i=0; i<board.length; i++){
            for(int j=0; j<board[0].length; j++){
                if(board[i][j]=='O'){
                    board[i][j]='X';
                }
                if(board[i][j]=='*'){
                    board[i][j]='O';
                }
            }
        }
    }

    private void dfs(int i, int j, char[][]board){
        if(i<0 || i>=board.length || j<0 || j>=board[0].length){
            return;
        }
        if(board[i][j]=='O'){
            board[i][j]='*';
            dfs(i-1, j, board);
            dfs(i+1, j, board);
            dfs(i, j-1, board);
            dfs(i, j+1, board);
        }
    }
}
```