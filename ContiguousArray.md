# Contiguous Array

```javascript
/**
 * Finds the longest contiguous subarray with an equal number of 0s and 1s
 * @param {number[]} nums - Array containing only 0s and 1s
 * @return {number} Length of the longest contiguous subarray with equal 0s and 1s
 */
function findMaxLength(nums) {
    // Map to store running balance and its earliest occurrence index
    const balanceMap = new Map();
    balanceMap.set(0, -1);  // Initialize with balance 0 at index -1
    
    let longestSubarray = 0;
    let balance = 0;  // Running balance: +1 for 1s, -1 for 0s

    for (let i = 0; i < nums.length; i++) {
        // Update balance: increment for 1, decrement for 0
        balance += nums[i] === 1 ? 1 : -1;
        
        if (balanceMap.has(balance)) {
            // If we've seen this balance before, we found a valid subarray
            const subarrayLength = i - balanceMap.get(balance);
            longestSubarray = Math.max(longestSubarray, subarrayLength);
        } else {
            // Record the first occurrence of this balance
            balanceMap.set(balance, i);
        }
    }

    return longestSubarray;
}

// Example usage
console.log(findMaxLength([0, 1, 0, 1]));  // Output: 4
``` 

# Problem Description

Given an array containing only 0s and 1s, find the longest contiguous subarray with an equal number of 0s and 1s.

## Example

Input: `[0, 1, 0, 1]`
Output: `4`

## Approach

The key insight is to track a running balance:
- Add +1 for each 1 encountered
- Subtract -1 for each 0 encountered

When we see the same balance twice, it means we've found a subarray with equal 0s and 1s.

## Step-by-Step Walkthrough

Let's walk through the example `[0, 1, 0, 1]`:

1. Start with balance = 0 at index -1 (before array starts)

2. Index 0: `0` 
   - Balance = -1
   - Record balance -1 at index 0

3. Index 1: `1`
   - Balance = 0 
   - We've seen balance 0 before at index -1
   - Length = 2 (from index -1 to 1)

4. Index 2: `0`
   - Balance = -1
   - We've seen balance -1 before at index 0
   - Length = 2 (from index 0 to 2)

5. Index 3: `1`
   - Balance = 0
   - We've seen balance 0 before at index -1
   - Length = 4 (from index -1 to 3)

Final answer: 4 (the entire array is balanced)

## Valid Examples

1. Simple alternating: `[0, 1]`
   - Equal number of 0s and 1s

2. Non-alternating: `[0, 1, 1, 0]`
   - Two 0s and two 1s = balanced

3. Grouped pattern: `[1, 1, 0, 0]`
   - Two 1s followed by two 0s = balanced

## Invalid Examples

1. Unbalanced counts: `[1, 1, 0]`
   - Two 1s and one 0 = not balanced

2. Non-contiguous: Cannot skip elements
   - In `[0, 1, 0, 1]`, cannot take `[0, 1]` and skip to last `1`

## Key Points

- Subarray must be contiguous (elements next to each other)
- Number of 0s must equal number of 1s
- Pattern does not need to alternate