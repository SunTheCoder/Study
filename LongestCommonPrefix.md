# Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

 

Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
 

Constraints:

1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lowercase English letters if it is non-empty.


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


---

## Longest Common Prefix

### **Understanding the Problem**

To find the longest common prefix among an array of strings, we compare characters across all strings until we find a mismatch.

### 🚀 **Key Insight:**
- The algorithm checks **each character** of the first string against all other strings.
- The check stops **as soon as a mismatch is found**, which makes the algorithm efficient in practice.

### **Complexity:**
- **Best Case:** Early mismatch → fast exit.
- **Worst Case:** All strings are identical → checks every character.

### ✅ **Optimized Approach:**

```javascript
var longestCommonPrefix = function(strs) {
    if (!strs.length) return "";

    let prefix = "";
    const minLength = Math.min(...strs.map(str => str.length)); // Optimize by limiting to the shortest string

    for (let i = 0; i < minLength; i++) {
        const char = strs[0][i];

        for (let j = 1; j < strs.length; j++) {
            if (strs[j][i] !== char) {
                return prefix;  // Early exit on mismatch
            }
        }
        prefix += char;
    }

    return prefix;
};
```

### **Why Early Exit Is Efficient:**
- If the first **1,000,000 strings** match, but the **1,000,001st string** doesn’t, the algorithm checks each character until the mismatch is found.
- **Early termination** reduces unnecessary checks.

### **Alternative Optimization (Sorting):**
- Sort the strings and compare only the **first and last strings**.
- This works because the common prefix of all strings must also be a prefix of these two.

```javascript
var longestCommonPrefix = function(strs) {
    if (!strs.length) return "";
    strs.sort();
    const first = strs[0], last = strs[strs.length - 1];
    let i = 0;
    while (i < first.length && first[i] === last[i]) {
        i++;
    }
    return first.slice(0, i);
};
```

This ensures efficiency even with large datasets.