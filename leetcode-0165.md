## 思路
- 根据`.`分割后逐一比较，不存在的取0

```java
class Solution {
    public int compareVersion(String version1, String version2) {
        String[] v1 = version1.split("\\.");
        String[] v2 = version2.split("\\.");
        int index=0;
        while(index<v1.length || index<v2.length){
            int num1 = index >= v1.length ? 0 : Integer.parseInt(v1[index]);
            int num2 = index >= v2.length ? 0 : Integer.parseInt(v2[index]);
            if(num1 > num2) return 1;
            if(num1 < num2) return -1;
            index++;
        }
        return 0;
    }
}
```