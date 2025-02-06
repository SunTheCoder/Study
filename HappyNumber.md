202. Happy Number
Solved
Easy
Topics
Companies
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

Starting with any positive integer, replace the number by the sum of the squares of its digits.
Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
Those numbers for which this process ends in 1 are happy.
Return true if n is a happy number, and false if not.

 

Example 1:

Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
Example 2:

Input: n = 2
Output: false
 

Constraints:

1 <= n <= 231 - 1

## Steps

1. Initialize a set to store the numbers we have seen.
2. Initialize a new number to the input number.
3. While the new number is not 1 and we have not seen it before, add it to the set and update the new number to the sum of the squares of its digits.
4. If the new number is 1, return true.
5. Otherwise, return false.

```javascript
var isHappy = function(n) {
    let seen = new Set()
    let newNum = n;

    while (newNum !== 1 && !seen.has(newNum)) {
        seen.add(newNum)
        
        let split = newNum.toString().split("")
        newNum = split.reduce((acc, num) => acc + (Number(num) * Number(num)), 0)
        
        console.log(newNum)
       
    }

    return newNum === 1
};
```

