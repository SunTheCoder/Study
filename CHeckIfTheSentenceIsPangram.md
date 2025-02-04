## Check if the Sentence is Pangram
#### O(n) space complexity O(n) time complexity

- Use a Set to store unique characters
- If the size of the Set is 26, then the sentence is a pangram
- If the size of the Set is less than 26, then the sentence is not a pangram
- If the size of the Set is greater than 26, then the sentence is not a pangram

```javascript
var checkIfPangram = function(sentence) {
    let uniqueCharacter = new Set(sentence)
    console.log(uniqueCharacter)
    
    if (uniqueCharacter.size === 26) return true
    return false
};
```