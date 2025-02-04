#Sliding Window Algorithm
    

## FindMaxAverage

```javascript
var findMaxAverage = function(nums, k) {
    // Calculate the sum of the first k elements
    let currSum = 0;
    for (let i = 0; i < k; i++) {
        currSum += nums[i];
    }

    // Set the initial max average
    let maxAvg = currSum / k;

    // Sliding window
    for (let right = k; right < nums.length; right++) {
        // Slide the window by subtracting the leftmost element and adding the new one
        currSum = currSum - nums[right - k] + nums[right];

        // Update the max average if the current window's average is larger
        maxAvg = Math.max(maxAvg, currSum / k);
    }

    return maxAvg;
};
