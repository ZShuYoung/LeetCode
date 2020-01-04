## 思路
- 从大到小开始遍历，注意int从1~3999
- 1000 100 10 1可以有多个；但是900 500 400 90 50 40 9 5 4只会有一个

```java
class Solution {
    public String intToRoman(int num) {
        StringBuilder sb = new StringBuilder();
        while(num>=1000){   //注意可以有多个
            sb.append("M");
            num-=1000;
        }
        if(num>=900){
            sb.append("CM");
            num-=900;
        }
        if(num>=500){
            sb.append("D");
            num-=500;
        }
        if(num>=400){
            sb.append("CD");
            num-=400;
        }
        while(num>=100){   //注意可以有多个
            sb.append("C");
            num-=100;
        }
        if(num>=90){
            sb.append("XC");
            num-=90;
        }
        if(num>=50){
            sb.append("L");
            num-=50;
        }
        if(num>=40){
            sb.append("XL");
            num-=40;
        }
        while(num>=10){   //注意可以有多个
            sb.append("X");
            num-=10;
        }
        if(num>=9){
            sb.append("IX");
            num-=9;
        }
        if(num>=5){
            sb.append("V");
            num-=5;
        }
        if(num>=4){
            sb.append("IV");
            num-=4;
        }
        while(num>=1){   //注意可以有多个
            sb.append("I");
            num-=1;
        }
        return sb.toString();
    }
}
```