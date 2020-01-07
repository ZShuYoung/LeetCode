## 思路
- 利用一个栈来帮助思考
- 遍历s的每个字符，如果是括号的左半边，就塞进栈内
- 如果是括号的右半边，那么和栈顶的字符匹配，如果是成对就把栈顶出栈（如果栈空那么直接返回false）
- 最后判断栈为空是也是有效的括号

```java
class Solution {
    public boolean isValid(String s) {
        if(s.length()==0){
            return true;
        }
        Stack<Character> stack = new Stack<>();
        for(int i=0;i<s.length();i++){
            char c = s.charAt(i);
            if(c=='(' || c=='[' || c=='{'){
                stack.push(c);
            }else if(c == ')'){
                if(stack.isEmpty() || stack.peek()!='('){
                    return false;
                }else{
                    stack.pop();
                }
            }else if(c == ']'){
                if(stack.isEmpty() || stack.peek()!='['){
                    return false;
                }else{
                    stack.pop();
                }
            }else{
                if(stack.isEmpty() || stack.peek()!='{'){
                    return false;
                }else{
                    stack.pop();
                }
            }
        }
        return stack.isEmpty();
    }
}
```