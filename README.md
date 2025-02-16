# Study

- <span style="color: red;">Resizing Arrays is expensive</span>

## Linked List

[Linked List](LinkedList.md)

[Middle of the Linked List](MiddleOfTheLinkedList.md)

[Linked List Cycle](LinkedListCycle.md)

[Delete Middle Node of a Linked List](DeleteMiddleNodeOfaLinkedList.md)

[Remove Duplicates from Sorted List](RemoveDuplicatesFromSortedList.md)


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

<span style="color: red;">Priority: High</span>

[Find Index of First Occurence in a String](FindIndexOfFirstOccurenceInAString.md)

### Distint Numbers in Each Subarray

<span style="color: red;">Priority: High</span>

[Distinct Numbers in Each Subarray](DistinctNumbersInEachSubArray.md)

- Time Complexity: O(n)
- Space Complexity: O(n)
- Used to find the number of distinct numbers in each subarray

## Two Pointers

[Two Pointers](TwoPointers.md)



## Prefix Sum


## Hash Table

<span style="color: red;">Priority: High</span>

[Sentence Similarity](SentenceSimilarity.md)

[Next Greater Element](NextGreaterElement.md)

## Stacks

<span style="color: red;">Priority: High</span>

[Stacks](Stacks.md)

[Simplify Path](SimplifyPath.md)

[IsValid](IsValid.md)

[Reverse Prefix of Word](ReversePrefixOfWord.md)

[Next Greater Element](NextGreaterElement.md)

[Moving Average from Data Stream](MovingAverageFromDataStream.md)

## Queue

[Queue](Queue.md)


