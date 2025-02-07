# Sentence Similarity

We can represent a sentence as an array of words, for example, the sentence "I am happy with leetcode" can be represented as arr = ["I","am",happy","with","leetcode"].

Given two sentences sentence1 and sentence2 each represented as a string array and given an array of string pairs similarPairs where similarPairs[i] = [xi, yi] indicates that the two words xi and yi are similar.

Return true if sentence1 and sentence2 are similar, or false if they are not similar.

Two sentences are similar if:

They have the same length (i.e., the same number of words)
sentence1[i] and sentence2[i] are similar.
Notice that a word is always similar to itself, also notice that the similarity relation is not transitive. For example, if the words a and b are similar, and the words b and c are similar, a and c are not necessarily similar.

 

Example 1:

Input: sentence1 = ["great","acting","skills"], sentence2 = ["fine","drama","talent"], similarPairs = [["great","fine"],["drama","acting"],["skills","talent"]]
Output: true
Explanation: The two sentences have the same length and each word i of sentence1 is also similar to the corresponding word in sentence2.
Example 2:

Input: sentence1 = ["great"], sentence2 = ["great"], similarPairs = []
Output: true
Explanation: A word is similar to itself.
Example 3:

Input: sentence1 = ["great"], sentence2 = ["doubleplus","good"], similarPairs = [["great","doubleplus"]]
Output: false
Explanation: As they don't have the same length, we return false.
 
## Steps

1. Check if the sentences have the same length.
2. Convert the similarPairs array into a Set for O(1) lookup.
3. Iterate through the sentences and check if the words are similar.


Constraints:

1 <= sentence1.length, sentence2.length <= 1000
1 <= sentence1[i].length, sentence2[i].length <= 20
sentence1[i] and sentence2[i] consist of English letters.
0 <= similarPairs.length <= 1000
similarPairs[i].length == 2
1 <= xi.length, yi.length <= 20
xi and yi consist of lower-case and upper-case English letters.
All the pairs (xi, yi) are distinct.

```javascript
/**
 * @param {string[]} sentence1
 * @param {string[]} sentence2
 * @param {string[][]} similarPairs
 * @return {boolean}
 */
var areSentencesSimilar = function(sentence1, sentence2, similarPairs) {
    if (sentence1.length !== sentence2.length) return false;

    // Convert similarPairs into a Set for O(1) lookup
    const similarSet = new Set(similarPairs.map(([a, b]) => `${a},${b}`));
    
    for (let i = 0; i < sentence1.length; i++) {
        if (
            sentence1[i] !== sentence2[i] && // If words are not the same
            !similarSet.has(`${sentence1[i]},${sentence2[i]}`) && // Check if they are a similar pair
            !similarSet.has(`${sentence2[i]},${sentence1[i]}`) // Also check reverse order
        ) {
            return false;
        }
    }

    return true;
}
```

