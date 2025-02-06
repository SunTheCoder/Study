# Largest Unique Number

```javascript

// Given an array of integers nums, return the largest integer that only occurs once. If no integer occurs once, return -1.

// Example 1:

// Input: nums = [5,7,3,9,4,9,8,3,1]    
// Output: 8
// Explanation: The maximum integer in the array is 9 but it occurs twice. The number 8 occurs only once, so it is the answer.

// Example 2:

// Input: nums = [9,9,8,8]  
// Output: -1
// Explanation: There is no integer that occurs once.

// Example 3:

// Input: nums = [1,2,3,4,5]    
// Output: 5
// Explanation: The number 5 occurs only once and is the largest number.

// Constraints:

// 1 <= nums.length <= 1000
// 1 <= nums[i] <= 1000


var largestUniqueNumber = function(nums) {
    const numMap = new Map()
    
    for (const num of nums) {
        
        numMap.set(num, (numMap.get(num) || 0) + 1)
    }
    console.log(numMap)
    
    let currMax = -Infinity
    
    for (const [key,  val] of numMap) {
        if (val === 1 && key > currMax) {
            currMax = key
        }
    }
    
    if (currMax === -Infinity) {
        return -1      
    }
    return currMax
       
};
```
