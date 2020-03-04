## 思路
- 这道题帮着进一步理解了BFS
- 为什么用BFS，因为污染橘子总是从周边开始，类似于层序遍历一样，所以使用BFS；而BFS普通需要使用队列做辅助，简单的伪代码如下：

```java
while queue 非空:
	node = queue.pop()
    for node 的所有相邻结点 m:
        if m 未访问过:
            queue.push(m)
```

### 对于本道题，思路如下
- 先遍历一遍二位数组，获取新鲜水果的个数，并把腐烂的水果放入队列
- 遍历完如果新鲜水果个数已经是0，那就没有必要再BFS了，直接返回0
- 如果新鲜的水果树不为0，并且腐烂队列中不为空，则做BFS搜索；每进入一次意味着一天

```java
class Solution {
    public int orangesRotting(int[][] grid) {
        int fresh = 0;
        int line=grid.length, row=grid[0].length;
        Queue<int[]> queue = new LinkedList<>();

        for(int i=0; i<line; i++){
            for(int j=0; j<row; j++){
                if(grid[i][j]==1){
                    fresh++;
                }else if(grid[i][j]==2){
                    queue.add(new int[]{i, j});
                }
            }
        }

        if(fresh==0) return 0;
        int ans = 0;
        while(fresh>0 && !queue.isEmpty()){
            ans++;
            // 这里要先取队列的值
            int n = queue.size();
            for(int i=0; i<n;i++){
                int[] location = queue.poll();
                int l = location[0];
                int r = location[1];
                if(l-1>=0 && grid[l-1][r]==1){
                    grid[l-1][r]=2;
                    fresh--;
                    queue.add(new int[]{l-1, r});
                }
                if(l+1<line && grid[l+1][r]==1){
                    grid[l+1][r]=2;
                    fresh--;
                    queue.add(new int[]{l+1, r});
                }
                if(r-1>=0 && grid[l][r-1]==1){
                    grid[l][r-1]=2;
                    fresh--;
                    queue.add(new int[]{l, r-1});
                }
                if(r+1<row && grid[l][r+1]==1){
                    grid[l][r+1]=2;
                    fresh--;
                    queue.add(new int[]{l, r+1});
                }
            }
        }
        return fresh==0 ? ans : -1;
    }
}
```