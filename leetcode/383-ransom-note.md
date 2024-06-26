---
title: Random Note
tags:
  - string
  - hash table
level: easy
date: 2024-06-17
link: https://leetcode.com/problems/ransom-note/
---

## 문제 요약

주어진 두 문자열 `ransomNote`와 `magazine`이 있을 때, `ransomNote`를 `magazine`의 문자들로 만들어질 수 있는지 여부를 반환하라.

## 접근 방법

해시 테이블에 저장해서 비교하는 방법과 magazine을 순회하면서 ransomNote의 문자를 찾아서 제거하는 방법이 있다.
`String.prototype.replace()`를 사용하면 magazine의 문자가 ransomNote에 존재하는지 파악할 수 있다.

### hash table을 이용한 방법

- `magazine`의 문자열을 해시 테이블에 저장한다.
- `ransomNote`의 문자열을 순회하면서, 해당 문자가 해시 테이블에 존재하는지 확인한다.
  - 존재하지 않는다면, `false`를 반환한다.
  - 존재한다면, 해당 문자를 해시 테이블에서 제거한다.
- 모든 문자를 순회했다면, `true`를 반환한다.

### magazine을 순회하면서 찾는 방법

- `magazine`을 순회하면서
  - `ransomNote`에서 해당 문자가 있으면 빈문자열로 제거한다. (`String.prototype.replace()`)
- `ransomNote`의 길이가 0이라면, `true`를 반환한다.
- `ransomNote`의 길이가 0이 아니라면, `false`를 반환한다.

## 코드

```js
// hash table(또는 객체)을 이용한 방법
var canConstruct = function(ransomNote, magazine) {
  const map = {}
  
  for (let char of magazine) {
    map[char] = (map[char] || 0) + 1
  }

  for (let char of ransomNote) {
    if (map[char]) {
      map[char]--
    } else {
      return false
    }
  }

  return true
};
```

```js
// string.prototype.replace 활용한 in-place 해결 방법
  var canConstruct = function(ransomNote, magazine) {
    for (let char in magazine) {
      ransomNote.replace(char, '')
    }
    return !ransomNote.length ? true : false
  }
```
