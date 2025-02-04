## Move Zeroes
#### O(n) space complexity O(n) time complexity

- Initialize an array to store zeroes
- Iterate through the array
- If the current element is 0, add it to the zeroes array
- If the current element is not 0, add it to the nums array
- Push the zeroes array to the end of the nums array

### My First Approach
```javascript
var moveZeroes = function(nums) {
    let zeroes = []

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === 0) {
            zeroes.push(0)
            nums.splice(i, 1)
            i--
        }
    }
    nums.push(...zeroes)
    console.log(nums)
    return nums
};
```

### Optimized Approach
#### O(1) space complexity O(n) time complexity

- Initialize an insertPos pointer to 0
- Iterate through the array
- If the current element is not 0, add it to the nums array
- If the current element is 0, increment the insertPos pointer
- Fill the remaining positions with zeros

```javascript
var moveZeroes = function(nums) {
    let insertPos = 0; // Pointer for the next non-zero position

    // Step 1: Move all non-zero elements to the front
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== 0) {
            nums[insertPos] = nums[i];
            insertPos++;
        }
    }

    // Step 2: Fill the remaining positions with zeros
    for (let i = insertPos; i < nums.length; i++) {
        nums[i] = 0;
    }
};
```