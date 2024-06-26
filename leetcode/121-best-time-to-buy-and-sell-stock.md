---
title: Best Time to Buy and Sell Stock
tags:
  - array
  - two pointers
level: easy
date: 2024-06-11
link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
---

## 문제 요약

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
주식을 사고 팔아서 가질 수 있는 가장 큰 이익을 찾는 문제이다.
배열의 요소는 각 날짜의 주식 가격이다. [첫쨋날, 둘째날, ...]
주식은 서로 다른날에 사고 팔 수 있으며 한번만 사고 팔 수 있다. 
이익이 없는 경우 0을 반환한다.

## 접근 방법 : Two Pointers

1. `buy` 와 `sell` 두개의 포인터를 선언하고 각각 0과 1로 초기값을 설정한다. (주식은 서로 다른날에 사고 팔 수 있으므로 첫쨋날과 둘째날을 기점으로 한다.)
2. `maxProfit` 변수를 선언하고 초기값을 0으로 설정한다.
3. `sell` 포인터가 배열의 끝까지 이동할때까지 반복한다.
   3-1. `buy > sell`  -> 이전 날보다 더 저렴하게? 매수할 수 있는 날을 발견했다! `buy`가 없데이트 되어야 함. (`buy` 포인터를 `sell` 포인터로 이동한다.)
   3-2. `buy < sell` -> 수익이 났다 - `sell` 포인터의 값과 `buy` 포인터의 값의 차이를 계산하여 `maxProfit`과 비교하여 큰 값을 저장한다.
   3-3. 3-1, 3-2가 종료되면 `sell++`로 포인터를 이동한다.
4. 반복이 끝나면 `maxProfit`을 반환한다.

## 스텝 바이 스텝

```
princes = [7, 1, 5, 3, 6, 4]
s = 0, b = 0, mp = 0  (각각 sell, buy, maxProfit)
```


```
[7, 1, 5, 3, 6, 4]    mp = 0
 |  |
 b  s
```
1. `buy` 포인터와 `sell` 포인터의 값을 비교한다.
  - `7`은 `1`보다 크므로 매수하려는 날(buy)을 `sell`의 위치로 이동한다.
  - `sell` 포인터를 한칸 이동한다. (`sell++`)


```
[7, 1, 5, 3, 6, 4]    mp = 4
    |  |
    b  s
```
2. `buy` 포인터와 `sell` 포인터의 값을 비교한다.
  - `1`은 `5`보다 작으므로 수익이 발생한다. `maxProfit`을 계산한다. (`5 - 1 = 4`)
  - 기존 `maxProfit` 0 과 비교하여 큰 값을 저장한다. (`mp = 4`)
  - `sell` 포인터를 한칸 이동한다. (`sell++`)


```
[7, 1, 5, 3, 6, 4]    mp = 4
    |     |
    b     s
```
3. `buy` 포인터와 `sell` 포인터의 값을 비교한다.
  - `1`은 `3`보다 작으므로 수익이 발생한다. `maxProfit`을 계산한다. (`3 - 1 = 2`)
  - 기존 `maxProfit` 4와 비교해 크지 않으므로 여전히 4가 된다. (`mp = 4`)
  - `sell` 포인터를 한칸 이동한다. (`sell++`)


```
[7, 1, 5, 3, 6, 4]    mp = 5
    |        |
    b        s
```
4. `buy` 포인터와 `sell` 포인터의 값을 비교한다.
  - `1`은 `6`보다 작으므로 수익이 나므로 `maxProfit`을 계산한다. (`6 - 1 = 5`)
  - 기존 `maxProfit`인 4와 비교하여 큰 값을 저장한다. (`mp = 5`)
  - `sell` 포인터를 한칸 이동한다. (`sell++`)


```
[7, 1, 5, 3, 6, 4]    mp = 5
    |           |
    b           s
```
5. `buy` 포인터와 `sell` 포인터의 값을 비교한다.
  - `1`은 `4`보다 작으므로 수익이 나므로 `maxProfit`을 계산한다. (`4 - 1 = 3`)
  - 기존 `maxProfit`인 5와 비교하여 큰 값을 저장한다. (`mp = 5`)
  - `sell` 포인터의 위치가 배열의 끝이므로 반복문을 종료한다.

6. `maxProfit`을 반환한다. (`5`)

## 코드

```js
function maxProfit(prices) {
  let buy = 0;
  let sell = 1;
  let maxProfit = 0;

  while (sell < prices.length) {
    if (prices[sell] < prices[buy]) {
      buy = sell;
    } else {
      maxProfit = Math.max(maxProfit, prices[sell] - prices[buy]);
    }
    sell++;
  }

  return maxProfit;
}
```

## 그외 다른 방법

```js
function maxProfit(prices) {
    let buyPrice = prices[0];
    let profit = 0;

    for (let i = 1; i < prices.length; i++) {
        if (buyPrice > prices[i]) {
            buyPrice = prices[i];
        }

        profit = Math.max(profit, prices[i] - buyPrice);
    }

    return profit;    
};

```

## 복잡도
이 방법은 한번의 순회로 해결할 수 있으므로 시간복잡도는 O(N)이다.
공간 복잡도는 O(1)이다.


