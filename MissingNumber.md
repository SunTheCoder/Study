## Missing Number
#### O(n) space complexity, O(n) time complexity

- Use a Set to store the numbers
- Iterate through the range of numbers
- If the number is not in the Set, return the number
- If the number is in the Set, increment the number
- Return the number

```javascript
var missingNumber = function(nums) {
    const n = nums.length;
    const range = Array.from({ length: n + 1 }, (_, i) => i); // Include 0 to n

    const numsSet = new Set(nums);

    for (const checkNum of range) {  // Use for...of to iterate values
        if (!numsSet.has(checkNum)) {
            return checkNum;  // Found the missing number
        }
    }
};
```

### **Why is `n + 1` Important?**

The range is generated using `Array.from({ length: n + 1 }, (_, i) => i)` to include **all numbers from 0 to n**. This is critical because:

- The array `nums` contains **n** elements, but the missing number could be **anywhere in the range [0, n]**.
- Without `+1`, the range would stop at `n - 1`, potentially **missing the largest number `n`** in the check.

For example:
- If `nums = [0, 1]`, the missing number is `2`. Without `n + 1`, the range would be `[0, 1]` and miss `2` entirely.

So, `n + 1` ensures we cover **all possible numbers** that could be missing.
