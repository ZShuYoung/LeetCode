## 基本思路
- 每行用一个StringBuilder去记录
- 定义down和up来遍历每一次从上到下和从下到上
- 注意循环中判断index越界

```java
class Solution {
    public String convert(String s, int numRows) {
        StringBuilder[] sbs = new StringBuilder[numRows];
        for(int i=0; i<numRows; i++){
            sbs[i] = new StringBuilder();
        }
        for(int i=0;i<s.length();){
            for(int down=0;down<numRows;down++){
                if(i<s.length()){
                    sbs[down].append(s.charAt(i++));
                }
            }
            for(int up=numRows-2;up>0;up--){
                if(i<s.length()){
                    sbs[up].append(s.charAt(i++));
                }
            }
        }
        StringBuilder res = new StringBuilder();
        for(StringBuilder sb : sbs){
            res.append(sb.toString());
        }
        return res.toString();
    }
}
```