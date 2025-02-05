## Scenario
Your task is to implement a simple container of integer numbers. You are given some template code in the Container class within the container.js file. You should implement any empty methods of this class, which correspond to the operations described below.

Unit tests are already implemented in the basicTests.js and containerTests.js files, so feel free to open them and get familiar with the details. Note that these unit tests use the mocha framework. To run these tests, you can use the following options associated with the RUN button located in the bottom-right corner:


If you'd like to receive a raw report of tests, choose the In Terminal option. The tests in this report will always be ordered in the same way, and will contain all debug output you've printed to the console.
If you'd like to receive test results with more structure, choose the Structured option. Note that debug output is not supported in this option.
If you'd like to run your project in a custom way, choose the Run Custom Script option. It will create a new main.sh file that is expected to contain the execution logic. The Run Custom Script button will execute this custom script when clicked.
The auto-generated main.sh file already contains a few examples that can be uncommented and executed
You can also use the following script to execute the first basic test only:
mocha specs -g 'Test basic 1'
For more information, check out the Readme tabon the left.
Partial credit will be granted for each unit test passed, so press Submit often to run tests and receive partial credits for passed tests. Please check tests for requirements and argument types.

Operations
The program starts with an empty container.

- ADD <value> should add the specified integer value to the container.

- DELETE <value> should attempt to remove the specified integer value from the container. If the value is present in the container, remove it and return true, otherwise, return false.

- GET_MEDIAN should return the median integer - the integer value in the middle of the sequence after all integer value stored in the container are sorted from smallest to largest. If the length of the sequence is even, the leftmost integer from the two middle integers should be returned. If the container is empty, this method should raise a runtime exception.

[execution time limit] 6 seconds

[memory limit] 1 GB


/**
 * A container of integers that supports
 * addition, removal, and search for the median integer
 */ 

```javascript
class Container {
  constructor() {
    this.data = []; // Store integers in a sorted manner
  }

  /**
   * Adds the specified value to the container
   * @param {number} value
   */
  add(value) {
    // Insert the value while maintaining sorted order
    let index = this.binarySearch(value);
    this.data.splice(index, 0, value);
  }

  /**
   * Attempts to delete one item of the specified value from the container
   * @param {number} value
   * @return {boolean} true, if the value has been deleted, or
   *                   false, otherwise.
   */
  delete(value) {
    let index = this.data.indexOf(value);
    if (index !== -1) {
      this.data.splice(index, 1);
      return true;
    }
    return false;
  }

  /**
   * Finds the container's median integer value, which is
   * the middle integer when all integers are sorted in order.
   * If the sorted array has an even length,
   * the leftmost integer between the two middle
   * integers should be considered as the median.
   * @return {number} the median if the array is not empty, or
   * @throws {Error} a runtime exception, otherwise.
   */
  getMedian() {
    if (this.data.length === 0) {
      throw new Error("The container is empty.");
    }

    const mid = Math.floor((this.data.length - 1) / 2);
    return this.data[mid];
  }

  /**
   * Helper function to find the correct index to insert a value
   * to maintain sorted order using binary search.
   * @param {number} value
   * @return {number} index where the value should be inserted
   */
  binarySearch(value) {
    let left = 0, right = this.data.length;
    while (left < right) {
      const mid = Math.floor((left + right) / 2);
      if (this.data[mid] < value) {
        left = mid + 1;
      } else {
        right = mid;
      }
    }
    return left;
  }
}

module.exports = Container;
```

## Explanation

- We use a binary search to find the correct index to insert the value
- We insert the value at the correct index
- We return the index
