### Tree Boundary Traversal

### Given a Binary Tree, find its Boundary Traversal. The traversal should be in the following order: 

### Left boundary nodes: defined as the path from the root to the left-most node ie- the leaf node you could reach when you always travel preferring the left subtree over the right subtree. 
### Leaf nodes: All the leaf nodes except for the ones that are part of left or right boundary.
### Reverse right boundary nodes: defined as the path from the right-most node to the root. The right-most node is the leaf node you could reach when you always travel preferring the right subtree over the left subtree. Exclude the root from this as it was already included in the traversal of left boundary nodes.
### Note: If the root doesn't have a left subtree or right subtree, then the root itself is the left or right boundary. 

Example 1:

Input:
        1 
      /   \
     2     3  
    / \   / \ 
   4   5 6   7
      / \
     8   9
   
Output: 1 2 4 8 9 6 7 3
Explanation:


 

Example 2:

Input:
            1
           /
          2
        /  \
       4    9
     /  \    \
    6    5    3
             /  \
            7     8

Output: 1 2 4 6 5 7 8
Explanation:


### Optimized solution

```java
//{ Driver Code Starts
import java.io.*;
import java.util.*;

class Node  
{ 
    int data; 
    Node left, right; 
   
    public Node(int d)  
    { 
        data = d; 
        left = right = null; 
    } 
}

class GFG
{
    static Node buildTree(String str)
    {
        // Corner Case
        if(str.length() == 0 || str.equals('N'))
            return null;
        String[] s = str.split(" ");
        
        Node root = new Node(Integer.parseInt(s[0]));
        Queue <Node> q = new LinkedList<Node>();
        q.add(root);
        
        // Starting from the second element
        int i = 1;
        while(!q.isEmpty() && i < s.length)
        {
              // Get and remove the front of the queue
              Node currNode = q.remove();
        
              // Get the current node's value from the string
              String currVal = s[i];
        
              // If the left child is not null
              if(!currVal.equals("N")) 
              {
        
                  // Create the left child for the current node
                  currNode.left = new Node(Integer.parseInt(currVal));
        
                  // Push it to the queue
                  q.add(currNode.left);
              }
        
              // For the right child
              i++;
              if(i >= s.length)
                  break;
              currVal = s[i];
        
              // If the right child is not null
              if(!currVal.equals("N")) 
              {
        
                  // Create the right child for the current node
                  currNode.right = new Node(Integer.parseInt(currVal));
        
                  // Push it to the queue
                  q.add(currNode.right);
              }
              
              i++;
        }
    
        return root;
    }
    
    public static void main(String args[]) throws IOException {
    
       BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(br.readLine().trim());
        while(t>0)
        {
            String s = br.readLine();
            Node root = buildTree(s);
            
            Solution T = new Solution();
            
            ArrayList <Integer> res = T.boundary(root);
            for (Integer num : res) System.out.print (num + " ");
            System.out.println();
            t--;
        }
    }
}

// } Driver Code Ends


//User function Template for Java

// class Node  
// { 
//     int data; 
//     Node left, right; 
   
//     public Node(int d)  
//     { 
//         data = d; 
//         left = right = null; 
//     } 
// }

class Solution
{
	ArrayList <Integer> boundary(Node node)
	{
	    ArrayList<Integer> boundaryTraversal = new ArrayList();
	    if(node.left==null && node.right== null) {
	        boundaryTraversal.add(node.data);
	        return boundaryTraversal;
	    }
	    boundaryTraversal.add(node.data);
	    findLeft(node.left, boundaryTraversal);
	    
	    findLeafs(node, boundaryTraversal);
	     
	    Stack<Integer> st = new Stack();
	    findRight(node.right, st);
	    
	    while(!st.isEmpty()){
	        boundaryTraversal.add(st.pop());
	    }
	    return boundaryTraversal;
	}
	public static void findLeft(Node node,  ArrayList<Integer> boundaryTraversal){
	   Node temp = node;
	   while(temp!=null){
	       if(!isLeaf(temp)) boundaryTraversal.add(temp.data);
	       if(temp.left!=null) temp = temp.left;
	       else temp = temp.right;
	   }
	}
	public static Node findLeafs(Node node , ArrayList<Integer> boundaryTraversal){
	    if(node==null) return null;
	    Node left = findLeafs(node.left, boundaryTraversal);
	     Node right = findLeafs(node.right, boundaryTraversal);
	     node.left = left;
	     node.right = right;
	     if(left==null && right==null) boundaryTraversal.add(node.data);
	     return node;
 	}
 	public static void findRight(Node node,Stack<Integer> stack ){
 	    Node temp = node;
 	    while(temp!=null){
 	        if(!isLeaf(temp)) stack.push(temp.data);
 	        if(temp.right!=null) temp = temp.right;
 	        else temp = temp.left;
 	    }
 	}
	public static boolean isLeaf(Node node){
	    if(node.right == null && node.left == null) return true;
	    return false;
	}
}

```














As you can see we have not taken the right subtree. 
Your Task:
This is a function problem. You don't have to take input. Just complete the function boundary() that takes the root node as input and returns an array containing the boundary values in anti-clockwise.

Expected Time Complexity: O(N). 
Expected Auxiliary Space: O(Height of the Tree).

Constraints:
1 ≤ Number of nodes ≤ 105
1 ≤ Data of a node ≤ 105

