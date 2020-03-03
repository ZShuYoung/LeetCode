## 思路

```java
class MinStack {
    private Stack<Integer> data;
    private Stack<Integer> min;
    
    /** initialize your data structure here. */
    public MinStack() {
        data = new Stack<>();
        min = new Stack<>();
    }
    
    public void push(int x) {
        data.push(x);
        if(min.isEmpty() || min.peek()>=x){
            min.push(x);
        }
    }
    
    public void pop() {
        if(data.pop().equals(min.peek())){
            min.pop();
        }
    }
    
    public int top() {
        return data.peek();
    }
    
    public int getMin() {
        return min.peek();
    }
}
```