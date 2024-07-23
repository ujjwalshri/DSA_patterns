### Merge two BST 's


### Given two BSTs, return elements of merged BSTs in sorted form.

Examples :

Input:
BST1:
       5
     /   \
    3     6
   / \
  2   4  
BST2:
        2
      /   \
     1     3
            \
             7
            /
           6
Output: 1 2 2 3 3 4 5 6 6 7
Explanation: After merging and sorting the two BST we get 1 2 2 3 3 4 5 6 6 7.
Input:
BST1:
       12
     /   
    9
   / \    
  6   11
BST2:
      8
    /  \
   5    10
  /
 2
Output: 2 5 6 8 9 10 11 12
Explanation: After merging and sorting the two BST we get 2 5 6 8 9 10 11 12.
Expected Time Complexity: O(m+n)
Expected Auxiliary Space: O(Height of BST1 + Height of BST2 + m + n)

Constraints:
1 ≤ Number of Nodes ≤ 105

### Approach 1
### 1. Do inorder traversal of both the BSTs and store the elements in two lists.
### 2. Merge the two lists and return the merged list.




```java
class Solution {
    // Function to return a list of integers denoting the node
    // values of both the BST in a sorted order.
    public List<Integer> merge(Node root1, Node root2) {
        // Write your code here
        ArrayList<Integer> list1 = new ArrayList();
        ArrayList<Integer> list2 = new ArrayList();
        helper(root1, list1);
        helper(root2, list2);
        ArrayList<Integer>ans = new ArrayList();
        int i =0; int j =0; int  k=0;
        while(i<list1.size() && j<list2.size()){
            if(list1.get(i) < list2.get(j)){
                ans.add(list1.get(i));
                
                i++;
            }else{
                ans.add(list2.get(j));
                
                j++;
            }
        }
        while(i<list1.size()){
            ans.add(list1.get(i));
            i++;
        }
        while(j<list2.size()){
            ans.add(list2.get(j));
            j++;
        }
        return ans;
    }
    public static void helper(Node root, ArrayList<Integer> list){
        if(root==null) return;
       
        helper(root.left, list);
         list.add(root.data);
        helper(root.right, list);
    }
    
}
```