# Middle of the Linked List

Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

## Steps

1. Initialize two pointers, slow and fast.
2. Move the fast pointer two nodes forward and the slow pointer one node forward.
3. When the fast pointer reaches the end of the list, the slow pointer will be at the middle of the list.
4. Return the slow pointer.
 
```javascript
var middleNode = function(head) {
    let slow = head;
    let fast = head;
   
    
    while (fast && fast.next) {
        slow = slow.next;
        
        fast = fast.next.next;
        
    }
    console.log(slow)
    return slow
    
};
```


