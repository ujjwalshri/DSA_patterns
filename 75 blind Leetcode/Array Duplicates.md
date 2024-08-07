### Array Duplicates

### Given an array arr of size n which contains elements in range from 0 to n-1, you need to find all the elements occurring more than once in the given array. Return the answer in ascending order. If no such element is found, return list containing [-1]. 

Examples:

Input: n = 4, arr[] = [0,3,1,2]
Output: -1
Explanation: There is no repeating element in the array. Therefore output is -1.
Input: n = 5, arr[] = [2,3,1,2,3]
Output: 2 3 
Explanation: 2 and 3 occur more than once in the given array.
Expected Time Complexity: O(n).
Expected Auxiliary Space: O(n).


```java 
//Brute force 
class Solution {
    public static ArrayList<Integer> duplicates(int[] arr) {
        // code here
     ArrayList<Integer> ans = new ArrayList();
     HashMap<Integer,Integer> map = new HashMap();
     for(int e : arr){
         map.put(e, map.getOrDefault(e, 0)+1);
     }
     for(int key : map.keySet()){
          if(map.get(key) > 1) ans.add(key);
     } 
     if(ans.isEmpty()) {
         ans.add(-1);
         return ans;
     }
     Collections.sort(ans);
     return ans;
    }
}
```

