### Search in Rotated Sorted Array


Search in Rotated Sorted Array
Difficulty: MediumAccuracy: 37.64%Submissions: 224K+Points: 4
Given a sorted (in ascending order) and rotated array arr of distinct elements which may be rotated at some point and given an element key, the task is to find the index of the given element key in the array arr. The whole array arr is given as the range to search.

Rotation shifts elements of the array by a certain number of positions, with elements that fall off one end reappearing at the other end.

Note:- 0-based indexing is followed & returns -1 if the key is not present.

Examples :

Input: arr[] = [5, 6, 7, 8, 9, 10, 1, 2, 3], key = 10
Output: 5
Explanation: 10 is found at index 5.
Input: arr[] = [3, 5, 1, 2], key = 6
Output: -1
Explanation: There is no element that has value 6.
Input: arr[] = [33, 42, 72, 99], key = 42
Output: 1
Explanation: 42 is found at index 1.
Expected Time Complexity: O(log n)
Expected Auxiliary Space: O(1)

Constraints:
1 ≤ arr.size() ≤ 106
0 ≤ arr[i] ≤ 106
1 ≤ key ≤ 105


### Binary Seach O(log n)
```java

class Solution {
    int search(int[] arr, int key) {
        // Complete this function
          //complete the function here
      int left = 0;
      
      int right = arr.length-1;
      while (left <= right){
          int mid = (left+right)/2;
          if(arr[mid] == key ) return mid;
          // Indentify the sorted halfs
          //right sorted
          if(arr[left] <= arr[mid]) { // left sorted
          if(arr[left] <= key && key<=arr[mid]){
              right = mid-1;
          }else{
              left = mid+1;
          }
              
          }else{
              // right sorted
             if(key >= arr[mid] && key<=arr[right]){
                 left = mid+1;
             }else{
                 right = mid-1;
             }
          }
          
          
      }
      return -1;
    }
}

```