```javascript
// Declaration: use the Map object
let hashMap = new Map();

// If you want to initialize it with some key value pairs, use the following syntax:
let hashMap = new Map([
    [1, 2],
    [5, 3],
    [7, 2]
]);

// Checking if a key exists: use .has()
hashMap.has(1); // true
hashMap.has(9); // false

// Accessing a value given a key: use .get()
hashMap.get(5); // 3

// Adding or updating a key: use .set()
// If the key already exists, the value will be updated
hashMap.set(5, 6);

// If the key doesn't exist yet, the key value pair will be inserted
hashMap.set(9, 15);

// Deleting a key: use .delete()
hashMap.delete(9);

// Get size
hashMap.size; // 3

// Iterate over the key value pairs: use the following code
for (const [key, value] of hashMap) {
    console.log(key + " " + value);
```

## Check if All Characters Have Equal Number of Occurrences

```javascript
var areOccurrencesEqual = function(s) {
    let counts = new Map();
    for (const c of s) {
        counts.set(c, (counts.get(c) || 0) + 1);
    }
    
    let frequencies = new Set();
    for (const val of counts.values()) {
        frequencies.add(val);
    }

    return frequencies.size == 1;
};
```

## Sets

- Great for unique values

```javascript
let uniqueValues = new Set();

uniqueValues.add(1);
uniqueValues.add(2);
```

## Hash Map

- Great for unique values

```javascript
let uniqueValues = new Set();
```