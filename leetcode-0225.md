## 思路
- 用两个队列来实现栈。
任何时候都只有一个队列有数据，另一个为空，当要执行pop或者top的时候才通过挪数据的形式返回结果

```java
class MyStack {
    private Queue<Integer> q1 = null;

    private Queue<Integer> q2 = null;

    /** Initialize your data structure here. */
    public MyStack() {
        q1 = new LinkedList<Integer>();
        q2 = new LinkedList<Integer>();
    }
    
    /** Push element x onto stack. */
    public void push(int x) {
        if(!q1.isEmpty()){
            q1.add(x);
        }else{
            q2.add(x);
        }
    }
    
    /** Removes the element on top of the stack and returns that element. */
    public int pop() {
        if(!q1.isEmpty()){
            while(q1.size()!=1){
                q2.add(q1.poll());
            }
            return q1.poll();
        }else{
            while(q2.size()!=1){
                q1.add(q2.poll());
            }
            return q2.poll();
        }
    }
    
    /** Get the top element. */
    public int top() {
        int topNumber = pop();
        if(!q1.isEmpty()){
            q1.add(topNumber);
        }else{
            q2.add(topNumber);
        }
        return topNumber;
    }
    
    /** Returns whether the stack is empty. */
    public boolean empty() {
        return q1.isEmpty() && q2.isEmpty();
    }
}
```