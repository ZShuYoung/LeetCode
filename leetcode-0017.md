## 思路：递归
- 当只有一个数字的时候很容易，如只有2，那么结果是["a","b","c"]; 如果只有3，那么结果是["d","e","f"]
- 当输入时ab的时候，其实结果是a和b结果的全排列
- 考虑这样的伪代码 `res(digits) = eachOf(res(digits(0,1))) * eachOf(res(digits(1)))`


```java
class Solution {
    public List<String> letterCombinations(String digits) {
        List<String> res = new ArrayList<>();
        if(digits.length()==0){
            return res;
        }else if(digits.length()==1){
            int num = Integer.valueOf(digits);
            switch(num){
                case 2:
                    return Arrays.asList("a","b","c");
                case 3:
                    return Arrays.asList("d","e","f");
                case 4:
                    return Arrays.asList("g","h","i");
                case 5:
                    return Arrays.asList("j","k","l");
                case 6:
                    return Arrays.asList("m","n","o");
                case 7:
                    return Arrays.asList("p","q","r","s");
                case 8:
                    return Arrays.asList("t","u","v");
                case 9:
                    return Arrays.asList("w","x","y","z");
            }
        }else{
            List<String> first = letterCombinations(digits.substring(0,1));
            List<String> second = letterCombinations(digits.substring(1));
            for(String f : first){
                for(String s : second){
                    res.add(f+s);
                }
            }
        }
        return res;
        
    }
}
```
