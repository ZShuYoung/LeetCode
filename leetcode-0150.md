## 思路
- 用栈记录数字，遇到算术符号了就取栈顶的两个数参与运算

```java
class Solution {
    public int evalRPN(String[] tokens) {
        int ans = 0;
        Stack<Integer> stk = new Stack<>();
        for(String str : tokens){
            if( "+".equals(str)){
                int second = stk.pop();
                int first = stk.pop();
                ans = first + second;
                stk.push(ans);
            }else if( "-".equals(str)){
                int second = stk.pop();
                int first = stk.pop();
                ans = first - second;
                stk.push(ans);
            }else if( "*".equals(str)){
                int second = stk.pop();
                int first = stk.pop();
                ans = first * second;
                stk.push(ans);
            }else if( "/".equals(str)){
                int second = stk.pop();
                int first = stk.pop();
                ans = first / second;
                stk.push(ans);
            }else{
                stk.push(Integer.parseInt(str));
            }
        }
        return stk.pop();
    }
}
```