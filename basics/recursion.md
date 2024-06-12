# Recursion (재귀)

재귀문은 함수가 자기 자신을 호출하는 것을 말한다. 재귀문은 반복문과 비슷한 역할을 하지만, 코드가 더 간결하고 이해하기 쉽다.
재귀문은 특히 트리 구조나 반복문으로 표현하기 어려운 문제를 해결할 때 유용하다. 재귀문은 반복문보다 느리고 메모리를 많이 사용한다는 단점이 있다.

## Base Case 와 Recursive Case

재귀문은 스스로를 호출하기 때문에 무한 루프에 빠지기 쉽다. 따라서 재귀문을 사용할 때는 반드시 종료 조건을 설정해야 한다.
종료 조건을 `Base Case`라고 하며, 이 조건이 만족되면 재귀문은 종료된다.
모든 재귀함수는 종료는 나타내는 `Base Case`와 재귀 호출(스스로를 호출하는 때)을 나타내는 `Recursive Case`로 구성된다.

```js
function sumRange(num) {
  if(num === 1) return 1; // Base Case - 종료되는 조건
  return num + sumRange(num-1) // Recursive Case - 스스로를 호출
}

sumRange(3)
// sumRange(3) => 3 + sumRange(2) => 2 + sumRange(1) => 1

```

 |   sumRange(1)  | -- return 1
 |   sumRange(2)  | -- return 2 + sumRange(1) => 3
 |   sumRange(3)  | -- return 3 + sumRange(2) => 6
 --- Call Stack ---

## Stack

재귀문을 이해하기 위해서는 프로그램의 실행 순서를 이해해야 한다. 재귀문은 스택(Stack) 자료구조를 사용한다.
Stack 자료구조는 LIFO(Last In First Out)로 동작한다. 즉, 가장 마지막에 들어온 데이터가 가장 먼저 나간다. 

예를 들어 쌓여있는 포스트잇을 생각해보자. 제일 위에 포스트잇을 떼어내거나(pop) 그 위에 새로운 포스트잇을 붙일 수 있다(push).
재귀문은 이런 식으로 동작한다. 재귀문이 실행될 때마다 스택에 함수가 쌓이고, 종료 조건이 만족되면 스택에서 함수가 하나씩 제거된다.

## Call Stack

- Any time a function is invoked it is placed (pushed) on the top of the call stack
- When JavaScript sees the return keyword or when the function ends, the compiler will remove (pop)
- The call stack is a stack data structure

## Pure Recursion

What is Pure Recursion?
A recursion function that does not use helper method or variables outside of the function itself.

- For arrays, use methods like `slice`, the spread operator, and `concat` that make copies of arrays so you do not mutate them
- Remember that strings are immutable so you will need to use methods like slice, substr, or substring to make copies of strings
- To make copies of objects use `Object.assign`, or the `spread operator`

```js
function collectOddValues(arr) {
  let newArr = [];

  if(arr.length === 0) {
    return newArr;
  }

  if(arr[0] % 2 !== 0) {
    newArr.push(arr[0]);
  }

  newArr = newArr.concat(collectOddValues(arr.slice(1)));
  return newArr;
}
```

## Helper Method Recursion

What is Helper Method Recursion?
A recursion function that has an outer function that is not recursive and an inner function that is recursive.

```js
function collectOddValues(arr) {
  let result = [];

  function helper(helperInput) {
    if(helperInput.length === 0) {
      return;
    }

    if(helperInput[0] % 2 !== 0) {
      result.push(helperInput[0]);
    }

    helper(helperInput.slice(1));
  }

  helper(arr);
  return result;
}
```
