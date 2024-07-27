### Form a palindrome

### Given a string, find the minimum number of characters to be inserted to convert it to a palindrome.

Examples :

Input: str = "abcd"
Output: 3
Explanation: Inserted character marked with bold characters in dcbabcd, here we need minimum three characters to make it palindrome.
Input: str = "aa"
Output: 0
Explanation: "aa" is already a palindrome.
Expected Time Complexity: O(n2)
Expected Auxiliary Space: O(n2)

Constraints:
1 ≤ |str| ≤ 500
str contains only lowercase alphabets.

Seen this question in a real interview before ?
Yes
No
Company Tags



### Java Solution using dynamic programming memoization
```java
class Solution{
    static int countMin(String str)
    { 
        StringBuilder sb = new StringBuilder(str);
        int LCPS = longestCommonSubsequence(str, sb.reverse().toString());
        return str.length() - LCPS;
        
      
    }
    public static int longestCommonSubsequence(String text1, String text2) {
        int[][]dp = new int[text1.length()][text2.length()];
        for(int[]e:dp){
            Arrays.fill(e,-1);
        }
        return helper(0, 0, text1, text2,dp);
        
    }
    public static int helper(int i , int j , String s1 , String s2,int[][]dp){
        if(i==s1.length() || j==s2.length()){
            return 0;
        }
        if(dp[i][j]!=-1) return dp[i][j];
        else if(s1.charAt(i)==s2.charAt(j)){
            return dp[i][j]=1+helper(i+1, j+1, s1, s2,dp);
        }else{
            return dp[i][j] =Math.max(helper(i+1, j,s1,s2,dp), helper(i,j+1,s1,s2,dp));
        }
}
    
}
```
