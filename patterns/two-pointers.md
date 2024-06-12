# Two Pointers Pattern

투 포인터 패턴은 주로 정렬된 배열이나 링크드리스트에서 두개의 각기 다른 포인터를 사용하여 특정 조건을 만족하는 요소를 찾는데 사용된다.
두개의 포인터는 서로 나란히 위치할 수도 있고, 서로 다른 방향에 위치할 수도 있다.
이 패턴은 대부분의 경우 시간복잡도 O(N)으로 해결할 수 있는것이 특징이다.

## 접근 방법

배열에서 중복요소를 제거하거나, 배열에서 합이 특정 값이 되는 요소를 찾는 문제에서 사용할 수 있다.
예를 들어 sumZero라는 함수가 있고 다음과 같은 조건이 있다고 해보자.

> 다음의 정렬된 배열에서 요소들 중 두개의 합에 0이 되는 첫번째 짝을 찾으시오. [-3, -2, -1, 0, 1, 2, 3] // [-3, 3]

가장 먼저 떠올릴 수 있는 Naive 접근 법은 배열을 순차적으로 돌면서 그 합이 0이 되는지 찾는것이다.

1. 배열의 처음부터 순회하면서 배열의 다음 요소와 합이 0이 되는지 찾는다.
2. 없는 경우 배열의 인덱스를 증가시켜 그값과 합이 0이 되는 값이 있는지 순회하면서 찾는다.
3. 있는 경우 반환한다.

이 경우, 무조건 배열을 전부 순회해야 하므로 중복 계산이 생기고 최악의 경우에는 시간복잡도가 O(N^2)이다.

```js
function sumZero(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length; j++>) {
      if (arr[i] + arr[j] === 0) {
        return [arr[i], arr[j]]
      }
    }
  }
}
```

주어진 배열이 정렬되어있다는 조건을 이용하여 투 포인터 패턴을 사용하면 시간복잡도를 O(N)으로 줄일 수 있다.
배열을 전부 순휘하는 대신 시작과 끝에서(가장 작은 값과 큰값) 비교를 통해 불필요한 순회를 줄일 수 있다.

1. 배열의 시작과 끝에 각각 두개의 포인터가 위치한다.
2. 왼쪽의 포인터가 오른쪽의 포인터보다 작을때까지 반복한다.
   1. 두 포인터의 합이 0보다 크면 오른쪽 포인터를 왼쪽으로 이동한다. -> 큰 값을 줄여야 함
   2. 두 포인터의 합이 0보다 작으면 왼쪽 포인터를 오른쪽으로 이동한다. -> 작은 값을 늘려야 함
   3. 두 포인터의 합이 0이면 두 포인터를 반환한다.

```js
function sumZero(arr) {
  let start = 0;
  let end = arr.length - 1;

  while (start < end) {
    let sum = arr[start] + arr[end];

    if (sum === 0) {
      return [arr[start], arr[end]];
    } else if (sum > 0) {
      end--;
    } else {
      start++;
    }
  }
}
```

## 문제 리스트

1. Two Sum https://leetcode.com/problems/two-sum/
1-1. Two Sum 2 - Input Array Is Sorted https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/
2. Remove Duplicates from Sorted Array https://leetcode.com/problems/remove-duplicates-from-sorted-array/
3. Remove Element https://leetcode.com/problems/remove-element/
4. Squaring a Sorted Array (easy) https://leetcode.com/problems/squares-of-a-sorted-array/
5. Triplet Sum to Zero (medium) https://leetcode.com/problems/3sum/
6. Triplet Sum Close to Target (medium) https://leetcode.com/problems/3sum-closest/
7. Triplets with Smaller Sum (medium) https://leetcode.com/problems/3sum-smaller/
8. Subarrays with Product Less than a Target (medium) https://leetcode.com/problems/subarray-product-less-than-k/
9. Dutch National Flag Problem (medium) https://leetcode.com/problems/sort-colors/
10. Quadruple Sum to Target (medium) https://leetcode.com/problems/4sum/
11. Comparing Strings containing Backspaces (medium) https://leetcode.com/problems/backspace-string-compare/
12. Minimum Window Sort (medium) https://leetcode.com/problems/shortest-unsorted-continuous-subarray/
