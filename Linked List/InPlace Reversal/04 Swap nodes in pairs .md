# Python Code


```python

class Solution:
    def swapPairs(self, head):
        """
        Swaps every two adjacent nodes in a linked list and returns the head of the modified list.
        
        Parameters:
            head (ListNode): The head of the linked list.
        
        Returns:
            ListNode: The head of the modified linked list after swapping adjacent nodes.
        """
        if not head or not head.next:
            return head

        currNode = head
        dummyNode = ListNode()  # Create a dummy node to handle the modified list
        linkingPointer = dummyNode

        while currNode and currNode.next:
            Next = currNode.next  # Next node to be swapped
            temp = Next.next  # Save the reference to the next pair
            
            # Swapping adjacent nodes
            Next.next = currNode
            linkingPointer.next = Next
            linkingPointer = currNode
            currNode = temp

        if not currNode:
            linkingPointer.next = None
        elif currNode and not currNode.next:
            linkingPointer.next = currNode
            currNode.next = None

        return dummyNode.next


```

**Time Complexity**
- The time complexity of the swapPairs method is O(n), where n is the number of nodes in the linked list. This is because we traverse through the entire list once, and for each pair of nodes, we perform constant-time operations to swap them.

**Space Complexity**
- The space complexity of the method is O(1) since we are not using any additional data structures that grow with the size of the input. We only use a constant amount of extra space to store a few pointers while performing the swaps. Hence, the space complexity is constant and does not depend on the size of the linked list.

# C++ Code
```cpp
class Solution {
public:
    /**
     * Swaps every two adjacent nodes in a linked list and returns the head of the modified list.
     *
     * @param head The head of the linked list.
     * @return The head of the modified linked list after swapping adjacent nodes.
     */
    ListNode* swapPairs(ListNode* head) {
        //If there are less than 2 nodes in the given linked list, no need to do anything,just return the list as it is.
        if (head == NULL || head->next == NULL) {
            return head;
        }

        ListNode* dummyNode = new ListNode(0, head);
        ListNode* prevNode = dummyNode;
        ListNode* currNode = head;

        while (currNode && currNode->next) {
            // Adjust the links to swap adjacent nodes
            prevNode->next = prevNode->next->next;
            currNode->next = currNode->next->next;

            // Reverse the link between the adjacent nodes
            prevNode->next->next = currNode;

            // Move iterators for the next iteration
            prevNode = currNode;
            currNode = currNode->next;
        }
        return dummyNode->next;
    }
};
```
