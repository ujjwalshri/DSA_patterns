### Missing number
```java
class Solution {
    public int missingNumber(int[] nums) {
        HashSet<Integer> set= new HashSet();
        for(int e : nums){
            set.add(e);
        }
        int n = nums.length;
        for(int i = 0;i<=n;i++){
            if(!set.contains(i) ) return i;
        }
        return -1;
    }
}
```


```java
class Solution {
    public int missingNumber(int[] nums) {
        // sum of n natural numbers 
        int n = nums.length;
        int sumOfAllNaturalNumbers =( n  * (n + 1) )/2; // sum of n natural numbers
        int sumOfCurrentArray = 0;
        for(int e : nums ){
            sumOfCurrentArray += e;
        }

        return sumOfAllNaturalNumbers-sumOfCurrentArray;

    }
}
```

```java
class Solution {
    public int missingNumber(int[] nums) {
        // sum of n natural numbers 
      
        int n = nums.length;
        int xor1 = 0;
        int xor2 = 0;
        for(int i = 0;i<=n;i++){
           xor1 = xor1 ^ i;
        }
        for(int e : nums ){
            xor2 = xor2 ^ e;
        }
        return xor1 ^ xor2;
        

    }
}
```