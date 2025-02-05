```javascript
var twoSum = function(numbers, target) {
    let left = 0 
    let right = numbers.length-1

    while (left < right) {
        let currSum = numbers[left] + numbers[right]
        if( currSum === target) {
            return [left + 1, right + 1]
        }
        if (currSum > target) {
            right--
        } 
        if (currSum < target) {
            left++
        }
    }
    
};
```
