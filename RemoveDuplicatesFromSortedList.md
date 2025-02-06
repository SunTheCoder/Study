# Remove Duplicates from Sorted List

Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

## Steps

1. Initialize a set to keep track of seen values.
2. Iterate through the linked list.
3. If the value is already in the set, remove the node by setting the next pointer of the previous node to the next pointer of the current node.
4. If the value is not in the set, add the value to the set and move to the next node.

```javascript
var deleteDuplicates = function(head) {
    const seen = new Set();
    let pointer = head;
    let pointerPrev = null; // Start as null to track the previous node
    
    while (pointer) {
        if (seen.has(pointer.val)) {
            pointerPrev.next = pointer.next; // Remove duplicate
        } else {
            seen.add(pointer.val); // Mark value as seen
            pointerPrev = pointer; // Move pointerPrev forward only when NOT deleting
        }
        
        pointer = pointer.next; // Always move pointer forward
    }

    return head;
};
```
