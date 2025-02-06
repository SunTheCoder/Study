# Study

## Sieve of Eratosthenes

[Sieve of Eratosthenes](SieveOfEratosthenes.md)

- Time Complexity: O(n log log n)
- Space Complexity: O(n)
- Used to find all prime numbers up to a given limit

```javascript
function sieveOfEratosthenes(n) {
  const isPrime = new Array(n + 1).fill(true);
  isPrime[0] = isPrime[1] = false;

  for (let i = 2; i * i <= n; i++) {
    if (isPrime[i]) {
      for (let j = i * i; j <= n; j += i) {
        isPrime[j] = false;
      }
    }
  } 

  const primes = [];
  for (let i = 2; i <= n; i++) {
    if (isPrime[i]) {
      primes.push(i);
    }
  } 

  return primes;
}   
``` 

## Sliding Window

[Sliding Window](SlidingWindow.md)

- Time Complexity: O(n)
- Space Complexity: O(1)
- Used to find the maximum or minimum sum of a subarray of a given size

## Two Pointers

[Two Pointers](TwoPointers.md)

- Time Complexity: O(n)
- Space Complexity: O(1)
- Used to find the maximum or minimum sum of a subarray of a given size

## Prefix Sum

[Prefix Sum](PrefixSum.md)

- Time Complexity: O(n)
- Space Complexity: O(n)
- Used to find the sum of a subarray of a given size
    