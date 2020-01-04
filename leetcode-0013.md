## 思路
- 与leetcode12相似，从string头开始遍历

```java
class Solution {
    public int romanToInt(String s) {
        int ans=0;
        while(s.startsWith("M")){
            ans+=1000;
            s=s.substring(1);
        }
        if(s.startsWith("CM")){
            ans+=900;
            s=s.substring(2);
        }
        if(s.startsWith("D")){
            ans+=500;
            s=s.substring(1);
        }
        if(s.startsWith("CD")){
            ans+=400;
            s=s.substring(2);
        }
        while(s.startsWith("C")){
            ans+=100;
            s=s.substring(1);
        }
        if(s.startsWith("XC")){
            ans+=90;
            s=s.substring(2);
        }
        if(s.startsWith("L")){
            ans+=50;
            s=s.substring(1);
        }
        if(s.startsWith("XL")){
            ans+=40;
            s=s.substring(2);
        }
        while(s.startsWith("X")){
            ans+=10;
            s=s.substring(1);
        }
        if(s.startsWith("IX")){
            ans+=9;
            s=s.substring(2);
        }
        if(s.startsWith("V")){
            ans+=5;
            s=s.substring(1);
        }
        if(s.startsWith("IV")){
            ans+=4;
            s=s.substring(2);
        }
        while(s.startsWith("I")){
            ans+=1;
            s=s.substring(1);
        }
        return ans;
    }
}
```