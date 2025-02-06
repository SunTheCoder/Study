# Tuple Same Product

Given a list of numbers, find the number of tuples that have the same product.

- Time Complexity: O(n^2)
- Space Complexity: O(n)
- Used to find the number of tuples that have the same product

```javascript
var tupleSameProduct = function(nums) {
    const frequency = new Map();
    let count = 0;

    // Step 1: Generate all unique pairs
    for (let i = 0; i < nums.length; i++) {
        for (let j = i + 1; j < nums.length; j++) {  
            let product = nums[i] * nums[j]; 

            // Step 2: Count valid tuples
            if (frequency.has(product)) {
                let existingPairs = frequency.get(product);
                count += existingPairs * 8; // Each new pair forms 8 valid permutations
                frequency.set(product, existingPairs + 1);
            } else {
                frequency.set(product, 1);
            }
        }
    }

    return count;
};
```

```javascript
// Example usage:
const nums = [2, 3, 4, 6, 8, 12];
console.log(tupleSameProduct(nums)); // Output: 4
```

```javascript
// Example usage:
const nums = [2, 3, 4, 6, 8, 12];
console.log(tupleSameProduct(nums)); // Output: 4
```

```javascript
count += existingPairs * 8;
```

# Key Idea
We are counting tuples that satisfy: a × b = c × d

Each new (a,b) pair that has the same product as an existing pair (c,d) can form multiple valid orderings in a tuple.

# Step-by-Step Breakdown
When we find a product that already exists in the map (`frequency.has(product)`), it means we have at least one previous pair (c,d) that shares the same product as our new pair (a,b).

## Valid Tuples
The two pairs (a,b) and (c,d) can be arranged in 8 different ways because order matters.

## Permutations Breakdown
Given two valid pairs:
- (a,b)
- (c,d)

A valid tuple can be represented in 8 different ways:
1. (a,b,c,d)
2. (a,b,d,c) 
3. (b,a,c,d)
4. (b,a,d,c)
5. (c,d,a,b)
6. (c,d,b,a)
7. (d,c,a,b)
8. (d,c,b,a)

Since the ordering of (a,b) matters, and the ordering of (c,d) matters, we get 8 total unique ways to arrange them.

# Why Multiply by existingPairs?
Each time we encounter a new (a,b) pair, it can pair up with every previous pair (c,d) that shares the same product.

- If existingPairs = 1, it means one previous pair exists, so we add 8 new tuples
- If existingPairs = 2, it means two previous pairs exist, so we add 16 new tuples
- And so on...

Thus, `count += existingPairs * 8;` ensures that all new tuples formed with the previous pairs are correctly counted.

# Example Walkthrough
Let's run tupleSameProduct([2,3,4,6]) step by step.

## Step 1: Compute Products
We find all pair products:

| Pair (a,b) | Product |
|------------|---------|
| (2,3)      | 6       |
| (2,4)      | 8       |
| (2,6)      | 12      |
| (3,4)      | 12      |
| (3,6)      | 18      |
| (4,6)      | 24      |

## Step 2: Process Each Pair
1. First Pair: (2,3), product = 6
   - Not seen before, frequency.set(6, 1)
   - No previous pairs → No tuples formed yet

2. Second Pair: (2,4), product = 8
   - Not seen before, frequency.set(8, 1)
   - No previous pairs → No tuples formed yet

3. Third Pair: (2,6), product = 12
   - Not seen before, frequency.set(12, 1)
   - No previous pairs → No tuples formed yet

4. Fourth Pair: (3,4), product = 12
   - frequency.get(12) == 1 (We've seen 12 before!)
   - We add 8 valid tuples
   - Update frequency.set(12, 2)

5. Fifth Pair: (3,6), product = 18
   - Not seen before, frequency.set(18, 1)
   - No previous pairs → No tuples formed yet

6. Sixth Pair: (4,6), product = 24
   - Not seen before, frequency.set(24, 1)
   - No previous pairs → No tuples formed yet

## Final Result
Only 12 appeared twice, forming 8 valid tuples.
Output: 8



