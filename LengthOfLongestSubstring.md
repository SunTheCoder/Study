## Length of Longest Substring (Sliding Window + MAP)

### Optimized Approach
#### O(n) space complexity O(n) time complexity
#### track characters and their latest indices using the Map data structure

- Initialize a Map to track characters and their latest indices
- Initialize a left pointer to the start of the string
- Initialize a maxLength variable to 0
- Iterate through the string
- If the character is already in the Map and its index is greater than or equal to the left pointer, move the left pointer past the duplicate
- Update the character's index in the Map

```javascript
var lengthOfLongestSubstring = function(s) {
    let charMap = new Map();  // To track characters and their latest indices
    let left = 0;             // Left boundary of the window
    let maxLength = 0;        // Result for the longest substring

    for (let right = 0; right < s.length; right++) {
        if (charMap.has(s[right]) && charMap.get(s[right]) >= left) {
            // Move the left pointer past the duplicate
            left = charMap.get(s[right]) + 1;
        }

        // Update the character's index
        charMap.set(s[right], right);

        // Update the maximum length
        maxLength = Math.max(maxLength, right - left + 1);
    }

    return maxLength;
};

```