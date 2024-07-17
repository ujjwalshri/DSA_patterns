### Construct Binary Tree from Parent Array


### Given an array parent that is used to represent a tree. The array indices (0-based indexing) are the values of the tree nodes and parent[i] denotes the parent node of a particular node. The parent of the root node would always be -1, as there is no parent for the root. Construct the standard linked representation of Binary Tree from this array representation and return the root node of the constructed tree.

### Note: If two elements have the same parent, the one that appears first in the array will be the left child and the other is the right child. You don't need to print anything, the driver code will print the level order traversal of the returned root node to verify the output.

Examples:

Input: parent[] = [-1, 0, 0, 1, 1, 3,5]
Output: 0 1 2 3 4 5 6
Explanation: the tree generated
will have a structure like 
          0
        /   \
       1     2
      / \
     3   4
    /
   5
 /
6
Input: parent[] = [2, 0, -1]
Output: 2 0 1
Explanation: the tree generated will
have a sturcture like
             2
            /   
           0      
          /   
         1     
Expected Time Complexity: O(n)
Expected Auxiliary Space: O(n)




### Solution 

```java
/*node class of the binary tree
class Node
{
    int data;
    Node left, right;
    Node(int key)
    {
        data = key;
        left = right = null;
    }
}*/
class Solution {
    // Function to construct binary tree from parent array.
    
    public Node createTree(int parent[]) {
        // Your code here
        // [0-1,2
        //  1-3,4
        //  3-5
        //  5-6
        // ]
        HashMap<Integer, ArrayList<Integer>> map = new HashMap();
        for(int i = 0;i<parent.length;i++){
            if(parent[i]!=-1 ){
                if(map.get(parent[i])==null){
                    ArrayList<Integer> temp = new ArrayList();
                    temp.add(i);
                    map.put(parent[i], temp);
                }else{
                    ArrayList<Integer> temp = map.get(parent[i]);
                    temp.add(i);
                    map.put(parent[i], temp);
                }
            }
        }
        int root = -1;
  
        for(int i = 0;i< parent.length;i++){
            if(parent[i]==-1){
                root = i;
            }
        }
        
    return buildTree(root,map);
    }
    public static Node buildTree(int root,HashMap<Integer,ArrayList<Integer>> map ){
   
       Node rootNode = new Node(root);
       if(map.get(root) != null &&  map.get(root).size() >=1 ){
           rootNode.left = buildTree(map.get(root).get(0), map);
       }
       if(map.get(root) != null && map.get(root).size() ==2){
           rootNode.right = buildTree(map.get(root).get(1), map);
       }
    
     return rootNode;
    }
}

```