### Given an array of integers and a sum B, find all unique combinations in the array where the sum is equal to B. The same number may be chosen from the array any number of times to make B.

## Note:
        1. All numbers will be positive integers.
        2. Elements in a combination (a1, a2, …, ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).
        3. The combinations themselves must be sorted in ascending order.


## First Approach 

##  intuition to avoid the repetitive making of the different combinations we have to make sure that we have only unique elements in the initial array 



```java
class Solution
{
    //Function to return a list of indexes denoting the required 
    //combinations whose sum is equal to given number.
    static ArrayList<ArrayList<Integer>> combinationSum(ArrayList<Integer> A, int B)
    {
        // add your code here
       
        HashSet<Integer> newA = new HashSet();
        for(int e: A){
            newA.add(e);
        }
        ArrayList<Integer> toSend = new ArrayList(newA);
        Collections.sort(toSend);
        ArrayList<ArrayList<Integer>> outer = new ArrayList();
        helper(0,toSend,B,new ArrayList(),outer);
        return outer;
    }
    public static void helper(int index, ArrayList<Integer> A, int B, ArrayList<Integer> curr,   ArrayList<ArrayList<Integer>> outer){
        
          if(B==0){
              outer.add(new ArrayList(curr));
              return;
          }
       
        for(int i = index;i<A.size();i++){
            if(A.get(i) <= B  ){
            curr.add(A.get(i));
            helper(i, A, B-A.get(i),curr, outer);
            curr.remove(curr.size()-1);
            }
            
        }
    
    }
    
}
```





## Second approach 


```java
class Solution
{
    //Function to return a list of indexes denoting the required 
    //combinations whose sum is equal to given number.
    static ArrayList<ArrayList<Integer>> combinationSum(ArrayList<Integer> A, int B)
    {
        // add your code here
         HashSet<Integer> newA = new HashSet();
        for(int e: A){
            newA.add(e);
        }
        ArrayList<Integer> toSend = new ArrayList(newA);
        Collections.sort(toSend);
        ArrayList<ArrayList<Integer>> outer = new ArrayList();
        helper(0,toSend,B,new ArrayList(),outer);
        return outer;
    }
    public static void helper(int index, ArrayList<Integer> A, int B, ArrayList<Integer> curr,   ArrayList<ArrayList<Integer>> outer){
        if(index >= A.size()){
          if(B==0){
              outer.add(new ArrayList(curr));
              return;
          }
          return;
          
        }
        
        // keep taking
        if(A.get(index) <= B){
        curr.add(A.get(index));
        helper(index,A,B-A.get(index),curr, outer);
        curr.remove(curr.size()-1);
        }
       
        // not take this and take next;
        helper(index+1, A,B, curr, outer);
        
    }
    
}
```