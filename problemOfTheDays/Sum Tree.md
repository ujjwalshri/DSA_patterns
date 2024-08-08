### Sum Tree


### Given a Binary Tree. Check for the Sum Tree for every node except the leaf node. Return true if it is a Sum Tree otherwise, return false.

### A SumTree is a Binary Tree where the value of a node is equal to the sum of the nodes present in its left subtree and right subtree. An empty tree is also a Sum Tree as the sum of an empty tree can be considered to be 0. A leaf node is also considered a Sum Tree.

Examples :

Input:
    3
  /   \    
 1     2
Output: true
Explanation: The sum of left subtree and right subtree is 1 + 2 = 3, which is the value of the root node. Therefore,the given binary tree is a sum tree.
Input:
          10
        /    \
      20      30
    /   \ 
   10    10
Output: false
Explanation: The given tree is not a sum tree. For the root node, sum of elements in left subtree is 40 and sum of elements in right subtree is 30. Root element = 10 which is not equal to 30+40.
Expected Time Complexity: O(n)
Expected Auxiliary Space: O(Height of the Tree)

Constraints:
1 ≤ number of nodes ≤ 105
1 ≤ node value ≤ 105



### DFS Approach
```java
class Solution {
    public static boolean ans = true;
    boolean isSumTree(Node root) {
        // Your code here
        ans = true;
        if(root== null) return true;
        if(root.left == null && root.right == null)  return true;
        helper(root);
        return ans;
    }
    public static Node helper(Node root){
        if(root== null) return root;
        Node left = helper(root.left);
        Node right = helper(root.right);
        if(left!= null && right == null){
           if(left.data + 0 != root.data) ans = false;  
        }else if(left == null && right != null){
            if( 0 + right.data != root.data) ans = false;
        }else if(left !=null && right!=null){
            if(left.data + right.data != root.data) ans = false;
        }
        
        root.left = left;
        root.right = right;
        root.data += (left == null )  ?  0 : left.data;
        root.data += (right == null ) ? 0 : right.data;
        return root;
    }
}
```