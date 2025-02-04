# Longest Common Prefix

```javascript
var longestCommonPrefix = function(strs) {
    if (!strs.length) return ""; // Edge case: empty array

    let prefix = "";

    for (let i = 0; i < strs[0].length; i++) {
        const char = strs[0][i]; // Reference character from the first string

        for (let j = 1; j < strs.length; j++) {
            // If the character doesn't match or we're out of bounds
            if (i >= strs[j].length || strs[j][i] !== char) {
                return prefix;
            }
        }

        // All strings have the same character at index i
        prefix += char;
    }

    return prefix;
};
```

## Explanation

- We iterate through the characters of the first string
- We check if the character matches the character in the other strings
- If it doesn't, we return the prefix
- If it does, we add the character to the prefix
- We return the prefix after we have iterated through all the characters

## Optimized Approach

```javascript
var longestCommonPrefix = function(strs) {
    if (!strs.length) return "";

    let prefix = "";
    const minLength = Math.min(...strs.map(str => str.length)); // Optimize by limiting to the shortest string

    for (let i = 0; i < minLength; i++) {
        const char = strs[0][i];

        for (let j = 1; j < strs.length; j++) {
            if (strs[j][i] !== char) {
                return prefix;
            }
        }
        prefix += char;
    }

    return prefix;
};
```

