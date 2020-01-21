## 思路
- 从右到左遍历，使用一个carry记录进位

```java
class Solution {
    public String addBinary(String a, String b) {
        int i=a.length()-1;
        int j=b.length()-1;
        StringBuilder sb = new StringBuilder();
        int carry = 0;
        while(i>=0 || j>=0){
            int currentA, currentB;
            int tempSum;
            if(i<0){
                currentA=0;
            }else{
                currentA = a.charAt(i) - '0';
            }
            if(j<0){
                currentB=0;
            }else{
                currentB = b.charAt(j) - '0';
            }
            tempSum = currentA + currentB + carry;
            sb.append(tempSum%2);
            carry = tempSum/2;
            i--;j--;
        }
        if(carry==1){
            sb.append(1);
        }
        return sb.reverse().toString();
    }
}
```