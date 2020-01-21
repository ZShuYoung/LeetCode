## 思路
- 先把path根据"/"分割开，用一个list记录最终的路径
- 遍历分隔后的数组，当为""或者"."的时候直接跳过
- 当为".."的时候需要先判断list是否为空，不为空的话删除最后一个路径
- 其他情况塞进list
- 最后list里面的路径就是简化后的路径

```java
class Solution {
    public String simplifyPath(String path) {
        List<String> list = new LinkedList<>();
        StringBuilder sb = new StringBuilder();
        String[] paths = path.split("/");
        for(String s : paths){
            if(s.equals(".") || s.equals("")){
                continue;
            }
            if(s.equals("..")){
                if(list.isEmpty()){
                    continue;
                }
                list.remove(list.size()-1);
            }else{
                list.add(s);
            }
        }
        for(String p : list){
            sb.append("/").append(p);
        }
        if(sb.length()==0){
            return "/";
        }
        return sb.toString();
    }
}
```