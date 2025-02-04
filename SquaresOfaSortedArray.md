## Squares of a Sorted Array (Two Pointers)
#### O(n) space complexity O(n) time complexity

- Initialize a result array to store the squares of the numbers
- Initialize a left pointer to the start of the array
- Initialize a right pointer to the end of the array
- Initialize a pos pointer to the end of the array
- Iterate through the array
- If the square of the left pointer is greater than the square of the right pointer, add the square of the left pointer to the result array and increment the left pointer
- If the square of the right pointer is greater than the square of the left pointer, add the square of the right pointer to the result array and decrement the right pointer

```javascript
var sortedSquares = function(nums) {
    let n = nums.length
    let left = 0
    let right = n - 1
    let pos = n -1
    
    const result = new Array(n)
    
    while (left <= right) {
        leftSquared = nums[left]**2
        rightSquared = nums[right]**2
        
        if (leftSquared > rightSquared) {
            result[pos] = leftSquared
            left++
        } else {
            result[pos] = rightSquared
            right--
        }
        pos--     
    }
    
    return result
}; 
```