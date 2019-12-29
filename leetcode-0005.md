## 中心扩散法

1. expandFromCenter接受两个参数，这样可以很方便处理"aba"和"abba"场景。
2. expandFromCenter循环结束后需要判断能形成回文串的两个边界

```java
class Solution {
    private int left=0;
    private int right=0;
    public String longestPalindrome(String s) {
        if(s.length()==0){
            return s;
        }
        for(int center=0;center<s.length();center++){
            expandFromCenter(center,center,s);
            expandFromCenter(center,center+1,s);
        }
        return s.substring(left,right+1);
    }

    private void expandFromCenter(int leftIndex, int rightIndex, String s){
        while(leftIndex>=0 && rightIndex<s.length() && s.charAt(leftIndex)==s.charAt(rightIndex)){
            leftIndex--;
            rightIndex++;
        }
        if(leftIndex<0){
            leftIndex++;
            rightIndex--;
        }else if(rightIndex==s.length()){
            leftIndex++;
            rightIndex--;
        }else if(s.charAt(leftIndex)!=s.charAt(rightIndex)){
            leftIndex++;
            rightIndex--;
        }
        if(rightIndex-leftIndex > right-left){
            left=leftIndex;
            right=rightIndex;
        }
    }
}
```

## 动态规划
d[i][j]为true表示下标i到j的子字符串是回文串，那么就可以有状态转移方程：
`d[i-1][j+1] = d[i][j] && s[i-1]=s[j+1]`。做一个循环，判断d[i][j]为true时对应的长度。

```java
class Solution {
    public String longestPalindrome(String s) {
        int n = s.length();
        if(n==0){
            return s;
        }
        int max=0;
        String ans=null;
        boolean[][] dp = new boolean[n][n];
        for(int i=n-1;i>=0;i--){
            for(int j=i;j<n;j++){
                dp[i][j] = s.charAt(i)==s.charAt(j) && ( j-i<3 || dp[i+1][j-1] );
                if(dp[i][j]){
                    if(j-i+1>max){
                        max = j-i+1;
                        ans = s.substring(i,j+1);
                    }
                }
            }
        }
        return ans;
    }
}
```