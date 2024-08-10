### Rotate a Linked List

Given a linked list, rotate the list to the right by k places, where k is non-negative.



Example 1:
Input: linkedlist: 2->4->7->8->9 , k = 3
Output: 8->9->2->4->7
Explanation:
Rotate 1: 4 -> 7 -> 8 -> 9 -> 2
Rotate 2: 7 -> 8 -> 9 -> 2 -> 4
Rotate 3: 8 -> 9 -> 2 -> 4 -> 7

Input: linkedlist: 1->2->3->4->5->6->7->8 , k = 4
Output: 5->6->7->8->1->2->3->4

Expected Time Complexity: O(n)
Expected Auxiliary Space: O(1)

Constraints:
1 <= number of nodes <= 103
1 <= node -> data <= 104
1 <= k <= number of node


### Most optimal  
```java
class Solution {
    // Function to rotate a linked list.
    public Node rotate(Node head, int k) {
        // add code here
        int length = 0;
        Node tail = head;
        while(tail.next!=null){
            length ++ ;
            tail = tail.next;
        }
        length++;
       k = k%length;

       while( k-->0 ){
          tail.next = head;
          tail = tail.next;
          head = head.next;
       } 
       tail.next = null;
       return head;
    }
   
}
```