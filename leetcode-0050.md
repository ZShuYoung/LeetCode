## 思路
- 递归
- `myPow(x,n)=myPow(x,n/2) * myPow(x, n/2) * myPow(x, n%2)` 
- 递归终止条件就是`n==0 or n==1 or n==-1`

```java
class Solution {
    public double myPow(double x, int n) {
        double ans = 1.0;
        if(n<0){
            x = 1/x;
        }
        while(n!=0){
            if(n%2!=0){
                ans = ans*x;
            }
            x = x*x;
            n /= 2;
        }
        return ans;
    }
}
```

---

- 迭代
- 这里不是一次一次的乘，而是平方平方地乘


```java
class Solution {
    public double myPow(double x, int n) {
        double ans = 1.0;
        if(n<0){
            x = 1/x;
        }
        while(n!=0){
            if(n%2!=0){
                ans = ans*x;
            }
            x = x*x;
            n /= 2;
        }
        return ans;
    }
}
```