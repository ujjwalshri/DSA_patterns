### Array to BST

### Given a sorted array. Convert it into a Height Balanced Binary Search Tree (BST). Return the root of the BST.

### Height-balanced BST means a binary tree in which the depth of the left subtree and the right subtree of every node never differ by more than 1.

### Note: The driver code will check the BST, if it is a Height-balanced BST, the output will be true otherwise the output will be false.

Examples :

Input: nums = [1, 2, 3, 4]
Output: true
Explanation: The preorder traversal of the following BST formed is [2, 1, 3, 4]:
           2
         /   \
        1     3
               \
                4
Input: nums = [1, 2, 3, 4, 5, 6, 7]
Ouput: true
Explanation: The preorder traversal of the following BST formed is [4, 2, 1, 3, 6, 5, 7]:
        4
       / \
      2   6
     / \   / \
    1 3  5 7
Expected Time Complexity: O(n)
Expected Auxillary Space: O(n)

Constraints:
1 ≤ nums.size() ≤ 105
1 ≤ nums[i] ≤ 105

### Optimize

```java
class Solution {
    public Node sortedArrayToBST(int[] nums) {
        // Code here
        int n = nums.length;
        return helper(nums, 0, n-1);
    }
    public static Node helper(int[]nums, int start, int end){
            if(start > end ) return null;
            int mid = (start+end)/2;
            Node root = new Node(nums[mid]);
            root.left = helper(nums, start, mid-1);
            root.right= helper(nums, mid+1, end);
            return root;
      
    }
}
```