
# Sieve of Eratosthenes

The Sieve of Eratosthenes is an efficient algorithm for finding all prime numbers up to a given limit. It works by iteratively marking the multiples of each prime number as composite, thereby identifying all prime numbers.

## Steps of the Sieve of Eratosthenes

1. Create an array of boolean values, initialized to true.  
2. Iterate from 2 to the square root of n
3. Mark multiples of i as false (not prime)
4. Collect all prime numbers    

```javascript
function sieveOfEratosthenes(n) {
  // Step 1: Create an array of boolean values, initialized to true
  const isPrime = new Array(n + 1).fill(true);
  isPrime[0] = isPrime[1] = false; // 0 and 1 are not prime numbers

  // Step 2: Iterate from 2 to the square root of n
  for (let i = 2; i * i <= n; i++) {
    if (isPrime[i]) {
      // Step 3: Mark multiples of i as false (not prime)
      for (let j = i * i; j <= n; j += i) {
        isPrime[j] = false;
      }
    }
  }

  // Step 4: Collect all prime numbers
  const primes = [];
  for (let i = 2; i <= n; i++) {
    if (isPrime[i]) {
      primes.push(i);
    }
  }

  return primes;
}

// Example usage:
console.log(sieveOfEratosthenes(30)); 
// Output: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
