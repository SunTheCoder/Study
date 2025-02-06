# Max Number of Balloons

// Given a string text, you want to use the characters of text to form as many instances of the word "balloon" as possible.

// You can use each character in text at most once. Return the maximum number of instances that can be formed.

// Example 1:   

// Input: text = "nlaebolko"
// Output: 1

// Example 2:   

// Input: text = "loonbalxballpoon"
// Output: 2

// Example 3:   

// Input: text = "leetcode"
// Output: 0

// Constraints: 

// 1 <= text.length <= 10^4
// text consists of lower case English letters only.




```javascript
var maxNumberOfBalloons = function(text) {
   
    let textCount = new Map()
    let balloonCount = new Map()
    
    let balloon = "balloon"
    
     if (text.length < balloon.length) return 0
    
    for (const c of balloon) {
        balloonCount.set(c, (balloonCount.get(c) || 0) + 1)
    }
    console.log("balloon", balloonCount)
    
    
    for (const c of text) {
        if (balloonCount.has(c)) {
            textCount.set(c, (textCount.get(c) || 0) + 1)
        }
    }
    console.log("textCount", textCount)
    
    let maxBalloons = Infinity; // Start with the highest possible value

    for (const [char, requiredCount] of balloonCount.entries()) {
        const availableCount = textCount.get(char) || 0;
        const possibleWords = Math.floor(availableCount / requiredCount);

        maxBalloons = Math.min(maxBalloons, possibleWords);
    }

    return maxBalloons === Infinity ? 0 : maxBalloons;
};
```