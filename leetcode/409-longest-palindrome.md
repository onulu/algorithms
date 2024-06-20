---
title: Longest Palindrome
tags:
  - string
  - hash-table
  - palindrome
level: easy
date: 2024-06-17
link: https://leetcode.com/problems/longest-palindrome
---

## 문제

주어진 문자열은 대소문자를 구분하며 이 문자열로 만들 수 있는 가장 긴 palindrome의 길이를 구하는 문제이다.

## 풀이

문자열에 사용된 문자가 짝수인 경우 팰린드롬으로 사용할 수 있으며 홀수 인 경우 사용할 수 있는 문자는 가운데 1개뿐이므로 홀수는 1개만 추가할 수 있다.
(실제 가장 긴 팰린드롬을 만드는게 아닌 긴 팰린드롬의 길이를 구한다는 것에 포인트가 있다.)

```js
  var longestPalindrome = function(s) {
    let count = 0
    let map = {}

    for (let char of s) {
      map[char] = (map[char] || 0) + 1

      if (map[char] % 2 === 0) {
        count += 2
      }
    }

    return s.length > count ? count + 1 : count
  };
```

```js
  var longestPalindrome = function(s) {
    const set = new Set()
    let count = 0

    for (let char of s) {
      if (set.has(char)) {
        set.delete(char)
        count+=2
      }else {
        set.add(char)
      }
    }

    return set.size ? res + 1 : res
  }
```
