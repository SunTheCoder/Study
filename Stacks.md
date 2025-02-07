A stack is an ordered collection of elements where elements are only added and removed from the same end. In the physical world, an example of a stack would be a stack of plates in a kitchen - you add plates or remove plates from the top of the pile. In the software world, a good example of a stack is the history of your current browser's tab. Let's say you're on site A, and you click on a link to go to site B, then from B you click on another link to go to site C. Every time you click a link, you are adding to the stack - your history is now [A, B, C]. When you click the back arrow, you are "removing" from the stack - click it once and you have [A, B], click it again and you have [A].

<span style="color: red;">Another term used to describe stacks is LIFO, which stands for last in, first out. The last (most recent) element placed inside is the first element to come out.</span>

Stacks are very simple to implement. Some languages like Java have built-in stacks. In Python, you can just use a list stack = [] and use stack.append(element) and stack.pop(). In fact, any dynamic array can implement a stack. Typically, inserting into a stack is called pushing and removing from a stack is called popping. Stacks will usually also come with operations like peek, which means looking at the element at the top of the stack.

The time complexity of stack operations is dependent on the implementation. If you use a dynamic array, which is the most common and easiest way, then the time complexity of your operations is the same as that of a dynamic array. 
O
(
1
)
O(1) push, pop, and random access, and 
O
(
n
)
O(n) search. Sometimes, a stack may be implemented with a linked list with a tail pointer.

The characteristic that makes something a "stack" is that you can only add and remove elements from the same end. It doesn't matter how you implement it, a "stack" is just an abstract interface.

Stacks and recursion are very similar. This is because recursion is actually done using a stack. Function calls are pushed on a stack. The call at the top of the stack at any given moment is the "active" call. On a return statement or the end of the function being reached, the current call is popped off the stack.

For algorithm problems, a stack is a good option whenever you can recognize the LIFO pattern. Usually, there will be some component of the problem that involves elements in the input interacting with each other. Interacting could mean matching elements together, querying some property such as "how far is the next largest element", evaluating a mathematical equation given as a string, just comparing elements against each other, or any other abstract interaction. Sometimes, the LIFO property is hard to see, but we'll make sure to talk about how we recognize it in this chapter.

![alt text](<Images/Screenshot 2025-02-06 at 8.42.56 PM.png>)
![alt text](<Images/Screenshot 2025-02-06 at 8.43.05 PM.png>)
![alt text](<Images/Screenshot 2025-02-06 at 8.43.12 PM.png>)
![alt text](<Images/Screenshot 2025-02-06 at 8.43.22 PM.png>)
![alt text](<Images/Screenshot 2025-02-06 at 8.42.43 PM.png>)




## Extra Notes

We are concerned about matching characters that will be adjacent to each other at any point in time. There could be two characters that will eventually be deleted, but not until other characters between them have been deleted first. The characters between them are "in the way".

When we use a stack, we keep a history of characters that are "in the way" of each other. For example, with "abccba", the c and b deletions are in the way of the a deletion.

After 3 iterations, the stack is ["a", "b", "c"]. Once the "c" is deleted, the next character in the stack is "ready" to be deleted. Once the "b" is deleted, the "a" is finally ready to be deleted.

The stack maintains the order for us. The main observation needed to recognize the stack solution is that the most recently seen character is the first one that needs to be deleted.

## Steps

1. Declare a stack.
2. Push elements onto the stack.
3. Pop elements from the stack.
4. Check if the stack is empty.
5. Check the element at the top of the stack.
6. Get the size of the stack.

```javascript
// Declaration: we will just use a list
let stack = [];

// Pushing elements:
stack.push(1);
stack.push(2);
stack.push(3);

// Popping elements:
stack.pop(); // 3
stack.pop(); // 2

// Check if empty:
!stack.length; // false

// Check element at top
stack[stack.length - 1]; // 1

// Get size
stack.length; // 1
```

```javascript
(function main() {
    let stack = [];
    
    stack.push(1);
    stack.push(2);
    stack.push(3);
    
    console.log(stack.pop());
    console.log(stack.pop());
    console.log(stack.pop());
    
    stack.push(5);
    
    if (!stack.length) {
        console.log("Stack is empty!");
    } else {
        console.log(`Stack is not empty, top is: ${stack[stack.length - 1]}`);
    }
}());
