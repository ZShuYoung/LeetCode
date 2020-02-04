## 思路
- BFS or DFS or 回溯
- 从每一个点开始进行BFS，用一个boolean[][] visited记录是否访问过
- 在BFS内部，如果cur（表示成功遍历的值）到底word的长度，那么返回true
- 如果越界，返回false
- 如果已经遍历过，返回false
- 如果当前点的字符与第word在cur位置上的不一致，返回false
- 不是以上情况的话，将visited置为true 并上下左右做BFS
- BFS结束的时候需要讲visited置为false（回溯的思想）

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        boolean[][] visited = new boolean[board.length][board[0].length];
        for(int i=0; i<board.length; i++){
            for(int j=0; j<board[0].length; j++){
                if(bfs(board, visited, i, j, word, 0)){
                    return true;
                }
            }
        }
        return false;
    }

    private boolean bfs(char[][] board, boolean[][] visited, int row, int column, String word, int cur){
        if(cur==word.length()){
            return true;
        }

        if(row<0 || row>board.length-1 || column<0 || column>board[0].length-1){
            return false;
        }
        
        if(visited[row][column]){
            return false;
        }

        if(board[row][column] != word.charAt(cur)){
            return false;
        }

        visited[row][column] = true;
        if(bfs(board, visited, row-1, column, word, cur+1)){
            return true;
        }
        if(bfs(board, visited, row+1, column, word, cur+1)){
            return true;
        }
        if(bfs(board, visited, row, column-1, word, cur+1)){
            return true;
        }
        if(bfs(board, visited, row, column+1, word, cur+1)){
            return true;
        }
        visited[row][column] = false;
        return false;
    }
}
```