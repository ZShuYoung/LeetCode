## 思路
- 从最后一位开始，先加1，再对10去膜，如果不为0说明不存在进位，直接返回
- 如果进位了，那么前一位也需要加1，所以再进入循环
- 如果循环结束说明最终有进位，那就new出来一个新的数字，第一位置1就行了

```java
class Solution {
    public int[] plusOne(int[] digits) {
        for(int i=digits.length-1; i>=0; i--){
            digits[i] += 1;
            digits[i] %= 10;
            if(digits[i] != 0){
                return digits;
            }
        }
        int[] ans = new int[digits.length+1];
        ans[0] = 1;
        return ans;
    }
}
```