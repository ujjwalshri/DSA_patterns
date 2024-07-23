### 
### Infix to Postfix
For Input: 
h^m^q^(7-4)
Your Output:
Exception in thread "main" java.lang.NullPointerException
	at Solution.infixToPostfix(File.java:47)
	at GFG.main(File.java:14)

Its Correct output is:
hm^q^74-^

```java
//{ Driver Code Starts
import java.util.*;
import java.lang.*;
import java.io.*;

class GFG {

    public static void main(String[] args) throws IOException {
        BufferedReader br =
            new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(br.readLine().trim());
        while (t-- > 0) {
            System.out.println(
                new Solution().infixToPostfix(br.readLine().trim()));
        }
    }
}
// } Driver Code Ends


class Solution {
    // Function to convert an infix expression to a postfix expression.
    public static String infixToPostfix(String exp) {
        // Your code here
        HashMap<Character, Integer> map = new HashMap();
        Stack<Character> stack = new Stack();
        map.put('^' , 3);
        map.put('*', 2);
        map.put('/', 2);
        map.put('+', 1);
        map.put('-', 1);
        map.put('(', -1);
 
        StringBuilder ans = new StringBuilder();
        for( char ch : exp.toCharArray()){
            if(Character.isLetterOrDigit(ch)){
                ans.append(ch);
            }else if(ch=='('){
               stack.push('(');
               
            }else if(ch==')'){
                while(stack.peek()!= '('){
                    ans.append(stack.pop());
                }
                stack.pop();
            }else{
                while(!stack.isEmpty() && map.get(ch) != null &&  map.get(ch) <= map.get(stack.peek())){
                  ans.append(stack.pop());
                }
                stack.push(ch);
            }
        }
        
        while(!stack.isEmpty()){
            ans.append(stack.pop());
        }
        return ans.toString();
    }
}
```