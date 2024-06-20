---
title: Two Sum
tags:
  - array
  - hash
level: easy
date: 2024-06-11
link: https://leetcode.com/problems/two-sum/
---


## 문제 요약

<https://leetcode.com/problems/two-sum/>
정수 배열과 정수 target이 주어진다. 배열에서 두개의 요소를 더하여 target이 되는 요소의 인덱스를 반환하라.

```text
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

Input: nums = [3,2,4], target = 6
Output: [1,2]
```

## 접근방법

### Brute force 방법

> 브루트 포스란 모든 경우의 수를 다 해보는 방법이다. 이 문제에서는 배열을 순차적으로 돌면서 두개의 요소를 더하여 target이 되는지 확인한다.

   1. 배열을 순회한다.
   2. i의 값과 다음 값(j)을 합쳐서 target이 되는지 확인한다.
      - 되면, 해당 요소의 인덱스와 다음 요소의 인덱스를 반환한다.
   3. j가 배열의 끝까지 가면 i를 다음 요소로 넘어간다. (i++)
   4. 반복한다.

### Hash Table 방법

   1. 배열을 순회한다.
   2. 현재 i의 값과 합쳤을때 target을 만들 수 있는 값에 해당하는 요소가 있는지 확인한다. (hashmap활용)
     - 있으면, 해당 요소의 인덱스와 현재 i의 인덱스를 반환한다.
     - 없으면, i를 다음 요소로 넘어간다.

## 스텝 바이 스텝

```text
Input: nums = [2,7,11,15], target = 13
```

```text
[2,7,11,15]     // target:13 - i:2 = 11
 |              // hash: {2:0} 
 i 
```

1. 현재 값인 2에 11을 더하면 타겟값인 13이 된다. 11이 hash에 있는지 체크하고 없으면 현재 인덱스와 값을 hash에 추가한다.
반복한다.

```text
[2,7,11,15]     // target:13 - i:7 = 6
   |            // hash: {2:0, 7:1} 
   i 
```

2. 7과 6이 합쳐져 13이 되므로 6이 hash에 있는지 확인한다.
없으므로 현재 인덱스와 값을 hash에 추가한다.

```text
[2,7,11,15]     // target 13 - 11 = 2
      |         // hash: {2:0, 7:1, 6:2} 
      i                   ^^^
```

3. 11과 2가 합쳐져 13이 되므로 2가 hash에 있는지 확인한다.
2가 있으므로 해당 인덱스`map.get(2)`와 현재 인덱스`i`를 반환한다.

## 코드

반복문이 한번만 사용되므로 시간복잡도가 O(N)이다.

```js
//hash table
var twoSum = function(nums, target) {
  const map = new Map();
  
  for (let i = 0; i < nums.length; i++) {
    const diff = target - nums[i];
    
    if (map.has(diff)) {
      return [map.get(diff), i];
    }
    
    map.set(nums[i], i);
  }
};
```

```js
// Brut force
// 중첩 for문을 사용하기 때문에 시간복잡도가 O(N^2)이 된다.
var twoSum = function(nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
};
```
