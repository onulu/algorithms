---
title: Merge Two Sorted Lists
tags:
  - array
  - linked list
level: easy
date: 2024-06-14
link: https://leetcode.com/problems/merge-two-sorted-lists/
---


## 문제 요약

<https://leetcode.com/problems/merge-two-sorted-lists/>
두개의 정렬된 싱글 링크드 리스트가 주어진다.두 리스트를 한개의 정렬된 리스트로 합치는 문제.
병합된 리스트는 두 리스트의 노드를 이어붙여 만들어지며 병합된 링크드 리스트의 헤드를 반환하면 된다.

문제에서 주어진 링크드 리스트를 이렇게 정의되어 있으며 val은 현재 노드의 값이고 next는 다음 노드를 가리키는 포인터이다.

```js
  function ListNode(val, next) {
    this.val = (val===undefined ? 0 : val)
    this.next = (next===undefined ? null : next)
  }
```

## 접근 방법

두개의 링크드 리스트에서 두개의 노드를 비교하여 작은 값을 가지는 리스트에 병합한다.
다음 노드를 재귀적으로 호출하여 더이상 값이 없을 때 까지 합쳐 나간다.

## 코드

```js
var mergeTwoLists = function(list1, list2) {
    if (!list1 || !list2) return list1 || list2

    if (list1.val < list2.val) {
        list1.next = mergeTwoLists(list2, list1.next)
        return list1
    } else {
        list2.next = mergeTwoLists(list1, list2.next)
        return list2
    }
};
```
