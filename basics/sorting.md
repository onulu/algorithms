
# Sorting

## Bubble Sort

버블정렬은 인접한 두 요소를 비교하여 정렬하는 방식이다. 선택 정렬과 다른 점 중 하나는 선택 정렬은 최소값을 찾아 앞으로 보내는 방식이라면, 버블 정렬은 최대값을 찾아 뒤로 보내는 방식이다. 버블정렬의 시간 복잡도는 O(n^2)이다.

### Bubble Sort 구현 방법

- 리스트의 첫번째 요소부터 시작한다.
- 현재 요소와 다음 요소를 비교한다.
- 현재 요소가 다음 요소보다 크다면 두 요소를 교환한다.
- 이를 리스트의 마지막 요소까지 반복한다.

---

## Selection Sort

선택정렬은 리스트를 정렬하는 간단한 알고리즘이다. 이 정렬 알고리즘은 리스트를 정렬된 부분과 정렬되지 않은 부분으로 나누어 정렬한다. 초기에는 정렬된 부분이 비어있고, 정렬되지 않은 부분이 전체 리스트이다. 선택 정렬은 최소값을 찾아 앞으로 보내는 방식이다.

시간 복잡도는 O(n^2)이다. n개의 요소를 가진 리스트에서 최소값을 찾기 위해 n-1번의 비교를 하고, 두번째로 작은 값을 찾기 위해 n-2번의 비교를 하고, 이를 반복하면 n(n-1)/2번의 비교를 하게 된다. 이는 O(n^2)이다.

### Selection Sort 구현 방법

- 리스트의 첫번째 요소를 최소값으로 가정한다.
- 리스트의 나머지 요소들을 순회하며 최소값을 찾고 그 값을 첫번째 요소와 비교해 더 작은 값을 첫번째 요소로 설정한다.
- 이후 두번째 요소를 최소값으로 가정하고 위 과정을 반복한다.
- 이를 리스트의 마지막 요소까지 반복한다.

---

## Insertion Sort

Insertion Sort is a simple sorting algorithm that builds the final sorted array (or list) one item at a time.
Insertion Sort는 삽입 정렬이라고도 불리며, 각 요소를 적절한 위치에 삽입하는 방식으로 정렬한다. 선택 정렬과 다른 점은 선택 정렬은 최소값을 찾아 앞으로 보내는 방식이라면, 삽입 정렬은 각 요소를 적절한 위치에 삽입하는 방식이다.

### Insertion Sort 구현 방법

- 리스트의 두번째 요소부터 시작한다.
- 현재 요소를 key로 설정한다.
- key보다 작은 요소들을 찾아 key를 삽입할 위치를 찾는다.
- key보다 큰 요소들을 한칸씩 뒤로 밀어낸다.
- key를 찾은 위치에 삽입한다.
- 이를 리스트의 마지막 요소까지 반복한다.

---

## Merge Sort

Merge Sort는 분할 정복(divide and conquer) 알고리즘 중 하나로, 리스트를 반으로 나누어 정렬하고 합치는 방식이다. 리스트를 반으로 나누어 정렬하는 과정을 재귀적으로 반복하며, 이후 정렬된 리스트를 합치는 과정을 거친다.

Merge Sort의 시간 복잡도는 O(n log n)이다.

### Merge Sort 구현 방법

- 리스트를 반으로 나눈다.
- 나눈 리스트를 정렬한다.
- 정렬된 리스트를 합친다.
  - 리스트를 합칠 때는 두 리스트의 첫번째 요소를 비교하여 작은 값을 결과 리스트에 추가한다.
  - 이후 비교한 요소는 리스트에서 제거하고, 이를 반복한다.
  - 두 리스트 중 하나가 비어있다면, 남은 리스트를 결과 리스트에 추가한다.


## Quick Sort

Quick Sort는 분할 정복 알고리즘 중 하나로, 리스트를 기준값(pivot)을 기준으로 작은 값은 왼쪽, 큰 값은 오른쪽으로 나누는 방식이다. 이후 나눈 리스트를 재귀적으로 정렬한다. Merge Sort와 다른점에는 Merge Sort는 리스트를 반으로 나누어 정렬하는 방식이라면, Quick Sort는 기준값을 기준으로 나누는 방식이다.

Quick Sort의 시간 복잡도는 O(n log n)이다.

### Quick Sort 구현 방법

- 리스트에서 기준값(pivot)을 선택한다.
- 리스트를 기준값을 기준으로 작은 값은 왼쪽, 큰 값은 오른쪽으로 나눈다.
- 나눈 리스트를 재귀적으로 정렬한다.
- 정렬된 리스트를 합친다.
- 이를 반복한다.
- 리스트의 길이가 1이하라면 정렬된 리스트를 반환한다.
- 리스트의 길이가 1이상이라면, 기준값을 기준으로 작은 값과 큰 값을 나누고, 재귀적으로 정렬한다.
