## Find Pivot Index
#### O(1) space complexity O(n) time complexity

- Calculate the total sum of the array
- Initialize the left sum to 0
- Iterate through the array
- Check if the left sum equals the total sum minus the left sum minus the current element
- If it does, return the current index
- If it doesn't, add the current element to the left sum
- Return -1 if no pivot index is found

```javascript

var pivotIndex = function(nums) {
    let totalSum = nums.reduce((acc, num) => acc + num, 0); // Calculate total sum
    let leftSum = 0; // Initialize left sum

    for (let i = 0; i < nums.length; i++) {
        // Check if leftSum equals rightSum
        if (leftSum === totalSum - leftSum - nums[i]) {
            return i; // Found the pivot index
        }
        leftSum += nums[i]; // Update the left sum
    }

    return -1; // If no pivot index is found
};
```