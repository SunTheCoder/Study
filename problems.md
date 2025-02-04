# Sliding Window Algorithm


## Squares of a Sorted Array 
#### O(n) space complexity O(n) time complexity

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
```

## Max Consecutive Ones III 
#### O(n) space complexity O(1) time complexity

```javascript

//the goal is to find the longest array of "1's" when we can flip k "0's" to "1"
var longestOnes = function(nums, k) {
    //curr is tracking the number of zeroes in current window
    let left = 0, curr = 0, ans = 0;
    for (let right = 0; right < nums.length; right++) {
        if(nums[right] == 0) {
            curr++;
        }
        while (curr > k) {
            /* while the current amount of zeroes is above k; we iterate from the left bound to switch the first occuring 0. when the left bound ios on a 1 it will increment up to keep incrementiin guntil it finds the first 0 so that the subarray can be valid again*/
            if (nums[left]=="0") {
                curr -= 1;
            }
            //was a 1 isntead of 0
            left++
        }
        
        ans = Math.max(ans, right - left + 1);
    }
    
    return ans
};
```

## Max Ascending Subarray Sum 
#### O(n) space complexity O(n) time complexity


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

## Running Sum of 1d Array
#### O(n) space complexity O(n) time complexity

```javascript
var runningSum = function(nums) {
    let prefix = [nums[0]];
    for (let i = 1; i < nums.length; i++) {
        prefix.push(nums[i] + prefix[prefix.length -1]);
    }
    return prefix
};
```
### Sencond Approach 
#### O(1) space complexity O(n) time complexity

```javascript
var runningSum = function(nums) {
    for (let i = 1; i < nums.length; i++) {
        nums[i] += nums[i - 1];  // Add the previous sum directly to the current element
    }
    return nums;
};
```

## Minimum Value to Get Positive Step by Step Sum
#### O(n) space complexity O(n) time complexity

```javascript
var minStartValue = function(nums) {
    let prefix = [nums[0]]; // Initialize prefix sum array

    // Build the prefix sum array
    for (let i = 1; i < nums.length; i++) {
        prefix[i] = prefix[i - 1] + nums[i];
    }

    // Find the minimum prefix sum
    let minPrefixSum = Math.min(0, ...prefix);

    // Calculate the minimum start value needed
    return 1 - minPrefixSum;
};
```

### Second Approach
#### O(1) space complexity O(n) time complexity

```javascript
var minStartValue = function(nums) {
    let minPrefixSum = 0; // To track the minimum prefix sum
    let currSum = 0;      // To track the current running sum

    for (let i = 0; i < nums.length; i++) {
        currSum += nums[i];               // Calculate the running sum
        minPrefixSum = Math.min(minPrefixSum, currSum); // Track the minimum sum
    }

    // To ensure the running sum is never less than 1
    return 1 - minPrefixSum;
};

```

## Find Pivot Index
#### O(1) space complexity O(n) time complexity

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











