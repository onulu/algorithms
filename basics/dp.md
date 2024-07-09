# Dynamic Programming

Dynamic Programming is a method for solving a complex problem by breaking it down into a collection of **simpler sub-problems**, solving each of those sub-problems just once, and **storing their solutions**.

1. Memoization
2. Tabulation

## example 1: fib(n)

```js
// Recursive solution
const fib = n => {
  if (n <= 2>) return 1
  return fib(n-1) + fib(n-2)
}
```

[Fib recursion tree](./images/dp_fib_rec.png)

Time complexity of the recursion solution is O(2^n). Because we are solving the same sub-problems multiple times.

let's improve the solution using memoization.

```js
const fib = (n, memo = {}) => {
  // store the result of the sub-problem
  if (n in memo) return memo[n]

  // base case
  if (n <= 2) return 1

  memo[n] = fib(n-1, memo) + fib(n-2, memo)
  return memo[n]
}
```

[Fib memoization tree](./images/dp_fib.png)

Time complexity of the memoization solution is O(n). Because we are storing the results of the sub-problems.

## example 2: Grid Traveler

Say that you are a traveler on a 2D grid. You begin in the top-left corner and your goal is to travel to the bottom-right corner. You may only move down or right.

```js
const gridTraveler = (m, n) => {
  if (n === 1 && n === 1) return 1;
  if (n === 0 || n === 0) return 0;

  // move right -> (m - 1, n) or move down -> (m, n - 1)
  return gridTraveler(m - 1, n) + gridTraveler(,m, n - 1)
}

```

[grid traveler recursion tree](./images/grid_rec.png)

Time complexity of the recursion solution is O(2^(n+m)). Because we are solving the same sub-problems multiple times.


let's improve the solution using memoization.

```js
const gridTraveler = (m, n, memo = {}) => {
  const key = m + ',' + n;
  if (key in memo) return memo[key];
  if (n === 1 && n === 1) return 1;
  if (n === 0 || n === 0) return 0;

  memo[key] = gridTraveler(m - 1, n, memo) + gridTraveler(m, n - 1, memo);
  return memo[key];
}
```

### Memoization Recipe

1. Make it work (brute force)
   - Visualize the problem as a tree
   - Implement the tree using recursion
   - Test it
2. Make it efficient
   - Add a memo object
   - Add a base case to return memo values
   - Store return values into the memo

## example 3: Can Sum

Write a function `canSum(targetSum, numbers)` that takes in a targetSum and an array of numbers as arguments.

The function should return a boolean indicating whether or not it is possible to generate the targetSum using numbers from the array.

```js
// brute force
const canSum = (targetSum, numbers) => {
  if (targetSum === 0) return true;
  if (targetSum < 0) return false;

  for (let num of numbers) {
    const remainder = targetSum - num;
    if (canSum(remainder, numbers) === true) {
      return true;
    }
  }

  return false;
}
```


```js
// memoization
const canSum = (targetSum, numbers, memo = {}) => {
  if (targetSum in memo) return memo[targetSum];
  if (targetSum === 0) return true;
  if (targetSum < 0) return false;

  for (let num of numbers) {
    const remainder = targetSum - num;
    if (canSum(remainder, numbers, memo) === true) {
      memo[targetSum] = true;
      return true;
    }
  }

  memo[targetSum] = false;
  return false;
}
```
