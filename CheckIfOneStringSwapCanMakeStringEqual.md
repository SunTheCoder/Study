```javascript
var areAlmostEqual = function(s1, s2) {
  
    let mismatchCount = 0
    let firstSwapIndex = -1
    let secondSwapIndex = -1
    
    if (s1 === s2) {
        return true
    }

    for (let pointer = 0; pointer < s2.length; pointer++) {
        if (s1[pointer] !== s2[pointer]) {
            if (firstSwapIndex === -1) {firstSwapIndex = pointer} else secondSwapIndex = pointer
            mismatchCount++ 
        }
    }

    let s1Array = s1.split("");

    // Perform the swap
    let temp = s1Array[firstSwapIndex];
    s1Array[firstSwapIndex] = s1Array[secondSwapIndex];
    s1Array[secondSwapIndex] = temp;

    // Convert back to string
    s1 = s1Array.join("");
    console.log(s1)

    if (mismatchCount === 2 && s1 === s2) return true
    return false

};
```
