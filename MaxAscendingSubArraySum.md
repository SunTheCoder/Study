## Max Ascending Subarray Sum 
#### O(n) space complexity O(n) time complexity

- Initialize the current sum to the first element
- Initialize the max sum to the first element
- Iterate through the array
- If the current element is greater than the previous element, add it to the current sum
- If the current element is less than the previous element, compare the current sum to the max sum and reset the current sum to the current element
- Return the max sum

```javascript
    // Since there's no fixed-length constraint (like k) and we're just looking for the maximum sum of strictly ascending subarrays, the single-pointer (or simple linear traversal) approach is the most efficient.
var maxAscendingSum = function(nums) {
    let currSum = nums[0];  // Initialize current sum with the first element
    let maxSum = nums[0];   // Track the maximum sum found so far

    for (let i = 1; i < nums.length; i++) {
        if (nums[i] > nums[i - 1]) { 
            // If current number is greater than the previous, continue the ascending sum
            currSum += nums[i];
        } else {
            // If the sequence breaks, compare and reset the current sum
            maxSum = Math.max(maxSum, currSum);
            currSum = nums[i]; // Start a new sum from the current element
        }
    }

    // Final comparison after the loop ends
    return Math.max(maxSum, currSum);
};
```