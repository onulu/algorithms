---
title: Valid Palindrome
tags:
  - string
  - two-pointer
level: easy
date: 2024-06-13
link: https://leetcode.com/problems/valid-palindrome/
---

## 문제 요약

https://leetcode.com/problems/valid-palindrome/
주어진 문자열이 팰린드롬인지 확인하라. 대소문자를 구분하지 않으며, 영문자와 숫자만을 대상으로 한다

## 접근 방법

palinrome 이란 앞으로 읽으나 뒤로 읽으나 같은 문자열을 말한다. 
따라서 주어진 문자열에서 불필요한 문자를 제거한 후 양쪽에 포인터를 두고 비교해서 확인 할 수 있다.

1. 문자열을 소문자로 변환한다.
2. 정규식을 사용하여 알파벳과 숫자가 아닌 문자열을 제거한다.
3. 양쪽에 포인터를 두고, 두 포인터가 만나기 전까지 포인터의 값을 비교한다.

## 코드

```js
var isPalindrome = function(s) {
    s = s.toLowerCase();
    s = s.replace(/[^a-z0-9]/g, '');
    
    let left = 0;
    let right = s.length - 1;
    while (left < right) {
        if (s[left] !== s[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
};
```

```js
var isPalindrome = function (s) {
    s = s.toLowerCase().replace(/[^a-z0-9]/g, '');
    for (let i = 0, j = s.length - 1; i < j; i++, j--) {
        if (s[i] !== s[j]) {
            return false;
        }
    }
    return true;
};
```

- 시간복잡도는 O(N)으로 문자열을 한번 순회하면서 비교한다.
- 공간복잡도는 O(1)로 상수만큼의 공간을 사용한다.
