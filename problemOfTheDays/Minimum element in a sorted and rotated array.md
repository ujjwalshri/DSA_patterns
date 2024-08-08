### Minimum element in a sorted and rotated array

### A sorted(in ascending order) array arr[ ] of size n with distinct elements is rotated at some unknown point, the task is to find the minimum element in it.

Examples:

Input:
n = 5, arr[] = {4 ,5 ,1 ,2 ,3}
Output: 1
Explanation: 1 is the minimum element in the array.
Input:
n = 7, arr[] = {10, 20, 30, 40, 50, 5, 7}
Output: 5
Explanation: Here 5 is the minimum element.
Expected Time Complexity: O(log n).
Expected Auxiliary Space: O(log n).

Constraints:
1 ≤ n ≤ 100000
1 ≤ arr[i] ≤ 1000000

### Approach Binary search O(log n)
```java
class Solution
{
    int findMin(int arr[], int n)
    {
        //complete the function here
        int l = 0;
        int r = arr.length-1;
        int ans = Integer.MAX_VALUE;
        while(l<=r){
            int mid = (l+r)/2;
            ans = Math.min(ans, arr[mid]);
            if(arr[mid] < arr[l]){
                r = mid-1;
                
            }else if(arr[l] <= arr[mid]){
                if( arr[r] <=arr[l])  l = mid+1;
                else r = mid-1;
            }
            
        }
        return ans;
    }
    
}
```
