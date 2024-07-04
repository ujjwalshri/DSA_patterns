### Duplicate Subtrees
 
 ## Given a binary tree, your task is to find all duplicate subtrees from the given binary tree.

## Duplicate Subtree : Two trees are duplicates if they have the same structure with the same node values.

## Note:  Return the root of each tree in the form of a list array & the driver code will print the tree in pre-order tree traversal in lexicographically increasing order.

## optimized code O(n^2)



```java
class Solution {
    public List<Node> printAllDups(Node root) {
        // code here
        HashMap<String,Integer> map = new HashMap();
         List<Node> ans = new ArrayList();
        checkDup(root,ans, map);
        return ans;
    }
    public static void  checkDup(Node root,List<Node> ans,HashMap<String,Integer> map){
         if(root==null) return;
         StringBuilder str = new StringBuilder();
         getPath(root, str);
         
         map.put(str.toString(), map.getOrDefault(str.toString(), 0)+1);
         if(map.get(str.toString())!=null && map.get(str.toString()) ==2) ans.add(root);
         checkDup(root.left, ans, map);
         checkDup(root.right,ans, map);
    }
     public static void getPath(Node root, StringBuilder str ) {
        if (root == null) return; // Use a special character to denote null
         
         str.append(root.data);
         getPath(root.left, str);
        
         getPath(root.right, str);
        // Preorder traversal to serialize the subtree
        
    }
    
}
```