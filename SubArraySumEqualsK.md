# Subarray Sum Equals K

- Use a hash map to store the cumulative sum and the number of times it has occurred
- If the cumulative sum minus k is in the hash map, it means there is a subarray that sums to k

```javascript
var subarraySum = function(nums, k) {
    let counts = new Map();
    counts.set(0, 1);
    let ans = 0, curr = 0;

    for (const num of nums) {
        curr += num;
        ans += counts.get(curr - k) || 0;
        counts.set(curr, (counts.get(curr) || 0) + 1);
    }

    return ans;
};
```

## Subarray Sum Equals K (Prefix Sum Approach)

### **Understanding Prefix Sums**

To find the number of subarrays that sum to `k`, we use the **prefix sum technique**. The prefix sum at index `i` represents the sum of all elements from the start of the array up to `i`.

### 🚀 **Key Insight:**
If we know the current prefix sum `curr` and want to find a subarray with sum `k`, we need to find if there was a **previous prefix sum** equal to `curr - k`. This is because:

```
curr - previous_prefix = k  ⟶ rearranged as ⟶ previous_prefix = curr - k
```

### 🔍 **Concrete Example:**

```javascript
nums = [1, 2, 1, 2, 1], k = 3
Prefix Sums: [1, 3, 4, 6, 7]
```

- At **i = 1** (prefix sum = 3), we directly have a subarray `[1, 2]` with sum = `k`.
- At **i = 2** (prefix sum = 4), we check if `4 - 3 = 1` exists in our prefix sum map—it does, indicating the subarray `[2, 1]`.
- This process repeats, counting all valid subarrays.

### **Why Initialize `{0: 1}` in the HashMap?**

We initialize the hash map with `{0: 1}` to account for subarrays that **start from the very beginning of the array**. Without this, we would miss cases where the prefix sum itself equals `k`.

### ✅ **Final Algorithm Outline:**

1. Maintain a running `curr` (current prefix sum).
2. For each number in `nums`:
   - Add to `curr`.
   - Check if `curr - k` exists in the map (indicating a valid subarray).
   - Add `curr` to the map.

This approach ensures **O(n) time complexity** with efficient subarray detection.