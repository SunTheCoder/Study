# Distinct Numbers in Each Subarray

Given an integer array nums and an integer k, you are asked to construct the array ans of size n-k+1 where ans[i] is the number of distinct numbers in the subarray nums[i:i+k-1] = [nums[i], nums[i+1], ..., nums[i+k-1]].

Return the array ans. 

Example 1:

Input: nums = [1,2,3,2,2,1,3], k = 3
Output: [3,2,2,2,3]
Explanation: The number of distinct elements in each subarray goes as follows:
- nums[0:2] = [1,2,3] so ans[0] = 3
- nums[1:3] = [2,3,2] so ans[1] = 2
- nums[2:4] = [3,2,2] so ans[2] = 2
- nums[3:5] = [2,2,1] so ans[3] = 2
- nums[4:6] = [2,1,3] so ans[4] = 3
Example 2:

Input: nums = [1,1,1,1,2,3,4], k = 4
Output: [1,2,3,4]
Explanation: The number of distinct elements in each subarray goes as follows:
- nums[0:3] = [1,1,1,1] so ans[0] = 1
- nums[1:4] = [1,1,1,2] so ans[1] = 2
- nums[2:5] = [1,1,2,3] so ans[2] = 3
- nums[3:6] = [1,2,3,4] so ans[3] = 4
 

Constraints:

1 <= k <= nums.length <= 105
1 <= nums[i] <= 105

## Steps

1. Initialize a frequency map to store the frequency of each number in the current window.
2. Initialize an array to store the number of distinct numbers in each subarray.
3. Iterate through the array and add the number to the frequency map.
4. If the size of the frequency map is equal to k, add the size of the frequency map to the result array.
5. If the size of the frequency map is greater than k, remove the number from the frequency map.
6. Return the result array.

```javascript
var distinctNumbers = function(nums, k) {
    const ans = [];
    const frequency = new Map();

    // Initialize frequency map for the first window
    for (let i = 0; i < k; i++) {
        frequency.set(nums[i], (frequency.get(nums[i]) || 0) + 1);
    }
    ans.push(frequency.size);

    // Slide the window
    for (let i = k; i < nums.length; i++) {
        // Remove the element going out of the window
        frequency.set(nums[i - k], frequency.get(nums[i - k]) - 1);
        if (frequency.get(nums[i - k]) === 0) {
            frequency.delete(nums[i - k]);
        }

        // Add the new element coming into the window
        frequency.set(nums[i], (frequency.get(nums[i]) || 0) + 1);

        // Store the count of distinct numbers
        ans.push(frequency.size);
    }

    return ans;
};
```


