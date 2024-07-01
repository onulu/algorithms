# Tree

Tree는 연결된 노드의 계층 구조를 나타낼때 널리 사용되는 자료구조이다. 트리의 각 노드는 여러 하위 노드에 연결 될 수 있지만 부모가 없는 루트를 제외하고는 단 한개의 부모 노드에 연결되어야 한다.
그래프와 달리 트리는 방향이 없고 연결된 비순환 그래프다. 각 노트는 자체 하위 트리의 루트 노드와 같을 수 있으므로 재귀는 트리탐색에 유용한 기법이다.
트리는 일반적으로 파일 시스템, JSON, HTML 문서와 같은 계층적 데이터를 표현하는 데 사용된다.
Array, Linked List, Queue, Stack 등을 선형자료구조 라고 한다면, Tree는 비선형 자료구조이다.

## 용어

- `Root`: 트리에서 가장 최상위 노드
- `Child`: 연결되는 부모 노드가 있는 모든 노드
- `Parent`: 다른 노드에 대한 연결이 있는 모든 노드
- `Sibling`: 한 부모를 가지고 있는 노드
- `Leaf`: 자식 노드가 없는 모든 노드
- `Edge`: 노드를 연결하는 선 (간선)
- `Height`: 루트 노드에서 가장 깊은 노드까지의 거리 (height = level - 1)
- `Depth`: 노드에서 루트 노드까지의 거리
- `Level`: 트리의 특정 깊이 - 루트 노드의 레벨은 0 (level = depth + 1)

  height와 depth는 같은 의미로 사용되기도 하지만, depth는 루트 노드에서 특정 노드까지의 거리를 의미하고, height는 트리의 높이를 의미한다. 

## 종류

- `Binary Tree`: 각 노드가 최대 2개의 자식 노드를 가질 수 있는 트리
- `Binary Search Tree`: 모든 왼쪽 자식 노드가 부모 노드보다 작고, 모든 오른쪽 자식 노드가 부모 노드보다 큰 트리
- `Balanced Tree`: 모든 리프 노드의 높이가 같은 트리
- `Complete Tree`: 마지막 레벨을 제외한 모든 레벨이 완전히 채워진 트리
- `Full Tree`: 모든 노드가 0개 또는 2개의 자식 노드를 가진 트리
- `Perfect Tree`: 모든 리프 노드의 높이가 같고 모든 노드가 0개 또는 2개의 자식 노드를 가진 트리
- `Binary Heap`: 완전 이진 트리로, 부모 노드가 자식 노드보다 크거나 작은 트리
- `Trie`: 문자열 검색에 사용되는 트리
- `AVL Tree`: 이진 탐색 트리의 일종으로, 균형을 유지하는 트리 (높이 차이가 1 이하)
- `B Tree`: 균형을 유지하는 트리로, 데이터베이스와 파일 시스템에서 사용된다.

## Binary Tree

- 이진 트리는 각 노드가 최대 2개의 자식 노드를 가질 수 있는 트리다.

## Binary Search Trees

- 이진 탐색 트리는 모든 왼쪽 자식 노드가 부모 노드보다 작고, 모든 오른쪽 자식 노드가 부모 노드보다 큰 트리다.
- 이진 탐색 트리는 이진 트리의 일종이다.

## Tree Traversal

트리의 모든 노드를 방문하는 방법은 크게 두 가지로 나뉜다. 너비 우선 탐색(BFS)과 깊이 우선 탐색(DFS)이다.

- `Breadth First Search (BFS)`: 너비 우선 탐색
- `Depth First Search (DFS)`: 깊이 우선 탐색
  - `Pre-order`: 노드 -> 왼쪽 -> 오른쪽
  - `In-order`: 왼쪽 -> 노드 -> 오른쪽
  - `Post-order`: 왼쪽 -> 오른쪽 -> 노드

## BFS

Breadth First Search 는 너비 우선 탐색이라고 불리며,그래프(Graph) 자료구조에서 사용되는 탐색 알고리즘이다. 루트 노드에서 시작해서 **같은 레벨**에 있는 노드들을 먼저 탐색하는 방법이다.
BFS 는 큐(Queue) 자료구조를 사용하여 구현한다. 큐는 FIFO(First In First Out)로 동작한다. 즉, 먼저 들어온 데이터가 먼저 나간다.

### Applications

- Web Crawling
- Social Networking
- Network Broadcast
- Garbage Collection
- Model Checking
- Shortest Path

### Steps (Iteratively)

1. 큐를 생성하고 루트 노드를 큐에 추가한다. 방문한 노드를 저장할 빈 배열도 생성한다.(visited)
2. 큐가 비어있지 않은 동안 다음을 반복한다.
   1. 큐에서 노드를 하나 꺼내(dequeue) 방문한다. (visited 배열에 추가한다.)
   2. 노드의 왼쪽 자식이 있다면 큐에 추가한다.
   3. 노드의 오른쪽 자식이 있다면 큐에 추가한다.
3. 방문한 노드를 담은 visited를 반환한다.

```js
function bfs() {
  const visited = []
  const queue = []
  const node = this.root

  queue.push(node)

  while(queue.length) {
    node = queue.shift()
    visited.push(node.value)

    if (node.left) {
      queue.push(node.left)
    }

    if (node.right) {
      queue.push(node.right)
    }
  }

  return visited
}
```

## DFS

DFS는 **깊이 우선 탐색**

### DFS Orders

- preOrder: visit the node **before(pre)** -> visit node, left, right
- postOrder: visit the node **after(post)** -> left, right, visit node
- InOrder: visit the node in-between -> left, visit, right

```js
  // preOrder
  ...
  const visited = []

  function traverse(node) {
    visited.push(node.val)
    if (node.left) bfs(node.left)
    if (node.right) bfs(node.right)
  }

  traverse(this.root)
  return visited
...
```

```js
  // postOrder
  ...
  const visited = []

  function traverse(node) {
    if (node.left) bfs(node.left)
    if (node.right) bfs(node.right)
    visited.push(node.val)
  }

  traverse(this.root)
  return visited
...
```

```js
  // inOrder
  ...
  const visited = []

  function traverse(node) {
    if (node.left) bfs(node.left)
    visited.push(node.val)
    if (node.right) bfs(node.right)
  }

  traverse(this.root)
  return visited
...
```
