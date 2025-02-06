# Study

- <span style="color: red;">Resizing Arrays is expensive</span>

## Linked List

[Linked List](LinkedList.md)

[Middle of the Linked List](MiddleOfTheLinkedList.md)

[Linked List Cycle](LinkedListCycle.md)



## Sieve of Eratosthenes

<span style="color: red;">Priority: High</span>

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
## Tuple Same Product

<span style="color: red;">Priority: High</span>

[Tuple Same Product](TupleSameProduct.md)


## Sliding Window

### Distint Numbers in Each Subarray

<span style="color: red;">Priority: High</span>

[Distint Numbers in Each Subarray](DistintNumbersInEachSubarray.md)

- Time Complexity: O(n)
- Space Complexity: O(n)
- Used to find the number of distinct numbers in each subarray

## Two Pointers

[Two Pointers](TwoPointers.md)



## Prefix Sum

[Prefix Sum](PrefixSum.md)

## Stack

### isValid

<span style="color: red;">Priority: High</span>

[IsValid](IsValid.md)

- Time Complexity: O(n)
- Space Complexity: O(n)
- Used to check if a string is valid


🔍 Why Does slowPrev.next = slow.next Modify head?
We need to remember that JavaScript objects (including linked list nodes) are reference types. That means when we change slowPrev.next, we are modifying the actual linked list in memory.