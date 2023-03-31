# Algorithm stuff

algorithm stuff

## 1. write a javascript function to return all combinations of k elements from an array of n elements.

Sure, here's a JavaScript function that takes an array of n elements and a value k, and returns all possible combinations of k elements from the array:

```js
function getCombinations(array, k) {
  const results = [];

  function recursiveHelper(combination, start) {
    if (combination.length === k) {
      results.push(combination.slice());
      return;
    }
    for (let i = start; i < array.length; i++) {
      combination.push(array[i]);
      recursiveHelper(combination, i + 1);
      combination.pop();
    }
  }

  recursiveHelper([], 0);
  return results;
}
```

Here's an explanation of how it works:

- The function initializes an empty array called results to hold the combinations.
- The function defines a helper function called recursiveHelper that takes two parameters: the current combination being built and the starting index for the loop.
- If the current combination's length equals k, it's considered a valid combination and pushed to the results array.
- Otherwise, the helper function loops through the remaining elements in the array from the starting index.
  Each element is added to the current combination and the recursiveHelper function is called recursively with the new combination and the index of the next element.
- After the recursive call, the last element is removed from the combination using the pop() method.
- Finally, the getCombinations function calls recursiveHelper with an empty combination and a starting index of 0, and returns the results array containing all the combinations.
- Here's an example of how to use this function:

### what is the complexity of this algorithm ?

The time complexity of this algorithm is O(n choose k), which is also written as (n C k), where n is the number of elements in the input array and k is the size of the combinations to be generated. The space complexity is also O(n choose k), since that's the maximum number of possible combinations that can be generated.

The reason for the time complexity is that the algorithm needs to generate all possible combinations of size k from the input array. The formula for the number of combinations is n choose k, which is equal to n! / (k! _ (n - k)!). This means that the algorithm needs to perform n! / (k! _ (n - k)!) iterations to generate all possible combinations.

In practice, this means that the algorithm can be very slow for large input sizes, especially when k is close to n. However, there are some optimizations that can be made to improve the performance of the algorithm, such as early stopping when the number of remaining elements is less than the required number of elements to form a combination.
