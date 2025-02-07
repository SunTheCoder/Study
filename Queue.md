# Queues

While a stack followed a LIFO pattern, a queue follows FIFO (first in first out). In a stack, elements are added and removed from the same side. In a queue, elements are added and removed from opposite sides. Like with a stack, there are multiple ways to implement a queue, but the important thing that defines it is the abstract interface of adding and removing from opposite sides.

An example of a queue in the physical world is a line at a fast food restaurant. People leave the line when they finish ordering (from the front) and people enter the line from the back (opposite ends). The first people to enter the line will be the first ones that leave it (FIFO). An example of a queue in the practical software world would be any system that handles a job on a first come, first serve basis - for example, if multiple people are trying to use a printer at the same time.

Queues are trickier to implement than stacks if you want to maintain good performance. Like a stack, you could just use a dynamic array, but operations on the front of the array (adding or removal) are 
O
(
n
)
O(n), where 
n
n is the size of the array. Adding to a queue is called enqueue and deletions are called dequeue. If you want these operations to be 
O
(
1
)
O(1), you'll need a more sophisticated implementation.

One way to implement an efficient queue is by using a doubly linked list. Recall that with a doubly linked list, if you have the pointer to a node, you can add or delete at that location in 
O
(
1
)
O(1). A doubly linked list that maintains pointers to the head and tail (both ends, usually with sentinel nodes) can implement an efficient queue.

There is also a data structure called a deque, short for double-ended queue, and pronounced "deck". In a deque, you can add or delete elements from both ends. A normal queue designates adding to one end and deleting to another end.

<span style="color: red;">For algorithm problems, queues are less common than stacks, and the problems are generally more difficult. The most common use of a queue is to implement an algorithm called breadth-first search (BFS), which we will learn about in a future chapter. Outside of BFS, unlike stack, there aren't many problems whose main focus is a queue - we'll still look at a few examples, but keep in mind that a queue is mostly used to implement BFS.</span> 


// JavaScript doesn't have any built-in efficient queue
// We'll just have to use a normal array
```javascript
let queue = [];

// If you want to initialize it with some initial values:
let queue = [1, 2, 3];

// Enqueueing/adding elements:
queue.push(4);
queue.push(5);

// Dequeuing/removing elements:
queue.shift(); // 1
queue.shift(); // 2

// Check element at front of queue (next element to be removed)
queue[0]; // 3

// Get size
queue.length; // 3
```

```javascript
(function main() {
    let queue = [];
    
    queue.push(1);
    queue.push(2);
    queue.push(3);
    
    while (queue.length) {
        console.log(queue.shift());
    }
    
    if (!queue.length) {
        console.log("Queue is empty!");
    }
}());
```





