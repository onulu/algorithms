---
title: Valid Parentheses
tags:
  - string
  - stack
level: easy
date: 2024-06-12
link: https://leetcode.com/problems/valid-parentheses/
---

## 문제 요약

괄호로 이루어진 문자열이 주어진다. 이때 괄호가 올바르게 열리고 닫혔는지 확인하라.

- 열린 괄호는 같은 종류의 괄호로 닫혀야 한다.
- 열린 괄호는 올바른 순서로 닫혀야 한다.

```text
Input: s = "()"
Output: true

Input: s = "()[]{}"
Output: true

Input: s = "(]"
Output: false
```

## 접근 방법

괄호는 최근의 열린 순으로 닫혀야 한다는 조건에 주목하면 스택을 사용하여 해결할 수 있다.
`{`, `(`, `[` 가 나오면 스택에 `}`, `)`, `]` 각각의 닫힌 괄호를 넣는다.
닫힌 괄호가 나오면 가장 마지막에 추가된 스텍의 아이템과 비교해 같은지 확인한다.
같지 않으면 순서가 틀린 경우이므로 false를 반환한다.
마지막으로 스택이 비어있는지 확인한다. 

## 스텝 바이 스텝

## 코드

```js
var isValid = function(s) {
  const stack = []
  
  // 길이가 홀수인 경우 짝이 맞지 않으므로 false
  if (s.length % 2 !== 0) return false

  for (let i = 0; i < s.length; i++) {
    const char = s[i]
    
    switch (char) {
      case '(':
        stack.push(')')
        break
      case '{':
        stack.push('}')
        break
      case '[':
        stack.push(']')
        break
      default:
        if (stack.pop() !== char) {
          return false
        }
    }
  }
  // '((' 로 이루어진 경우 스택이 비어있지 않게 되므로 최종적으로 체크한다.
  return stack.length === 0
}
```
