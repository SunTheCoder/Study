
# Find Index of First Occurence in a String

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

## Steps

1. Initialize two pointers, left and right.
2. Initialize a variable to store the current substring.
3. Iterate through the haystack.
4. If the current substring is equal to the needle, return the left pointer.
5. If the current substring is not equal to the needle, move the right pointer forward.
6. If the current substring is equal to the needle, move the left pointer forward.
7. If the current substring is not equal to the needle, return -1.

```javascript
/**
 * @param {string} haystack
 * @param {string} needle
* @return {number}
 */
var strStr = function(haystack, needle) {
    let left = 0;
    let right = 0
    let curr = ""

    // for (let right = 0; right < haystack.length; right++) {

        while (curr.length <= needle.length) {
            curr += haystack[right]
            console.log(curr)
            
            if (curr === needle ) {
                return left
            }
            if (curr.length === needle.length) {
                curr = curr.slice(1)
                left++
            }
            right++
        }
    // }
    return -1

};
```
