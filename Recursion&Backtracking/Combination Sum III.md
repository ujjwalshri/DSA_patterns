### Combination Sum III

## Find all valid combinations of K numbers that sum upto to N such that the following conditions are true:

## Only number 1 through 9 are used.
## Each number is used atmost once.
## Return the list of all possible valid combinations.

## Note: The list must not contain the same combination twice, and the combinations returned in any order.


Example 1:

Input:
K = 3
N = 7
Output: { {1, 2, 4} }
Explanation: 
1+ 2+ 4 = 7
There are no other valid combinations.
 

Example 2:

Input:
K = 3
N = 9
Output: { {1, 2, 6}, {1, 3, 5}, {2, 3, 4} }
Explanation: 
1 + 2 + 6 = 9
1 + 3 + 5 = 9
2 + 3 + 4 = 9
There are no other valid combinations.
 

Example 3:

Input:
K = 4
N = 3
Output: { { } }
Explanation: There are no valid combinations.
Using 4 different numbers in the range {1, 9}, the smallest sum we can get is 1 + 2 + 3 + 4 = 10 and since 10 > 3, there are no valid combinations.
 

Your Task:
You don't need to read input or print anything. Your task is to complete the function combinationSum() which takes the integers K and N as parameters and returns a list of all possible valid combinations.

Expected Time Complexity: O(2K)
Expected Auxiliary Space: O(K)

Constraints:
1 ≤ K ≤ 9
1 ≤ N  ≤ 60


### Code

```java

class Solution {
    public static ArrayList<ArrayList<Integer>> combinationSum(int K, int N) {
        HashSet<ArrayList<Integer>> outer = new HashSet();
         helper(1,K,N,outer, new ArrayList());
        return new ArrayList(outer);
    }
    public static void helper(int index, int k, int n,HashSet<ArrayList<Integer>> outer , ArrayList<Integer> combination ){
       if(n==0 && k==0 ){
           outer.add(new ArrayList(combination));
           return;
       }
       
        //take 
        for(int i = index; i<=9;i++){
        if(i <= n){
        combination.add(i);
        helper(i+1,k-1,n-i,outer, combination );
        combination.remove(combination.size()-1);
        helper(i+1,k, n, outer, combination);
        }
            
        }
       
      
        
        
    }
}
```