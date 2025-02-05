# Shortest Word Distance

Given an array of strings wordsDict and two different strings that already exist in the array word1 and word2, return the shortest distance between these two words in the list.

 

Example 1:

Input: wordsDict = ["practice", "makes", "perfect", "coding", "makes"], word1 = "coding", word2 = "practice"
Output: 3
Example 2:

Input: wordsDict = ["practice", "makes", "perfect", "coding", "makes"], word1 = "makes", word2 = "coding"
Output: 1
 

Constraints:

2 <= wordsDict.length <= 3 * 104
1 <= wordsDict[i].length <= 10
wordsDict[i] consists of lowercase English letters.
word1 and word2 are in wordsDict.
word1 != word2

```javascript
var shortestDistance = function(wordsDict, word1, word2) {
    let firstIndex = -1;
    let secondIndex = -1;
    let minDistance = Infinity; // Track the minimum distance

    for (let i = 0; i < wordsDict.length; i++) {
        if (wordsDict[i] === word1) {
            firstIndex = i;
        } 
        if (wordsDict[i] === word2) {
            secondIndex = i;
        }

        // Check if both words have been found at least once
        if (firstIndex !== -1 && secondIndex !== -1) {
            minDistance = Math.min(minDistance, Math.abs(firstIndex - secondIndex));
        }
    }

    return minDistance;
};
```

## Explanation

- We iterate through the wordsDict array
- We check if the current word is word1 or word2
- If it is, we update the firstIndex or secondIndex
- We check if both words have been found at least once
- If they have, we calculate the distance between the two indices and update the minDistance
- We return the minDistance


