## 思路
- 递归
- 找到递归终点当n=1的时候返回1，当n=2的时候返回2
- 递归公式为 `climbStairs(n) = climbStairs(n-1) + climbStairs(n-2)`
- 很可惜会超时

```java
class Solution {
    public int climbStairs(int n) {
        if(n==1) return 1;
        if(n==2) return 2;
        return climbStairs(n-1)+climbStairs(n-2);
    }
}
```

---

- 迭代
- 根据 `climbStairs(n) = climbStairs(n-1) + climbStairs(n-2)` 从3到n开始计算

```java
class Solution {
    public int climbStairs(int n) {
       if(n==1) return 1;
       if(n==2) return 2;
       int ans = 0;
       int prePre=1, pre=2;
       for(int i=3; i<=n; i++){
           ans = pre + prePre;
           prePre = pre;
           pre = ans;
       }
       return ans;
    }
}
```