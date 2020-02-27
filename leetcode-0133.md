## 思路
- BFS
- 用一个队列缓存遍历的Node，用一个HashMap保存每一个Node和其克隆
- 对于每一个Node，如果不在map里面就放入map，并且为其做一次克隆；然后遍历Node的相邻Node，先判断是否在map中 不在就放入map并且放入队列（表示没有遍历过），然后当前Node的克隆的相邻Node就是这些相邻Node的克隆

```java
class Solution {
    public Node cloneGraph(Node node) {
        if(node==null) return null;
        Map<Node, Node> map = new HashMap<>();
        Queue<Node> q = new LinkedList<>();
        q.add(node);

        while(!q.isEmpty()){
            Node cur = q.poll();
            if(!map.containsKey(cur)){
                map.put(cur, new Node(cur.val));
            }

            for(int i=0; i<cur.neighbors.size(); i++){
                Node neighbor = cur.neighbors.get(i);
                if(!map.containsKey(neighbor)){
                    map.put(neighbor, new Node(neighbor.val));
                    q.add(neighbor);
                }

                map.get(cur).neighbors.add(map.get(neighbor));
            }
        }
        return map.get(node);
    }
}
```