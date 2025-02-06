#isValid

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const stack = [];
    const matching = { ")": "(", "]": "[", "}": "{" };

    for (const char of s) {
        if (char === "(" || char === "[" || char === "{") {
            stack.push(char);  // Push opening brackets
        } else {
            if (stack.length === 0 || stack.pop() !== matching[char]) {
                return false;  // Unmatched closing bracket
            }
        }
    }

    return stack.length === 0;  // If stack is empty, all brackets matched correctly
};

// Example test case
console.log(isValid("(){}}{"));  // Output: false
console.log(isValid("(){}[]"));  // Output: true
console.log(isValid("(]"));      // Output: false
console.log(isValid("{[]}"));    // Output: true
```
