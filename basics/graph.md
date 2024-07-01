# Graph

그래프는 노드(Node)와 노드 사이의 연결된 간선(Edge)으로 이루어진 자료구조이다. Tree 는 그래프의 한 종류이며, 그래프는 트리가 아닐 수 있다. 그래프는 방향성이 있을 수도 있고 없을 수도 있다. 또한 그래프는 순환 구조일 수도 있고 아닐 수도 있다. (Tree는 방향성이 있고 순환 구조가 없다.)

`G = (V, E)` -> Graph G consists of a finite set of vertices V(nodes) and a finite set of edges E(Connection).

## Types of Graph

1. Undirected Graph - 방향성이 없다. (A -> B 이면 B -> A)
2. Directed Graph - 방향성이 있다. (A -> B 이면 B -> A 는 아니다.)
3. Weighted Graph - edge에 가중치가 있다. (가중치는 최단 경로, 최소 비용 등을 구할 때 사용한다.)
4. Cyclic Graph - 순환 구조를 가진다. (A -> B -> C -> A)
5. Acyclic Graph - 순환 구조를 가지지 않는다. (A -> B -> C)

## Representations of Graph

그래프는 두 가지 방식으로 표현할 수 있다.

1. 인접 행렬(Adjacency Matrix)
2. 인접 리스트(Adjacency List)


### Adjacency Matrix (인접 행렬)

인접 행렬은 2차원 배열로 표현된다. 행은 출발 노드, 열은 도착 노드를 나타낸다. 만약 노드 A에서 노드 B로 이어지는 edge가 있다면, `matrix[A][B] = 1` 로 표현한다. 만약 가중치가 있다면 `matrix[A][B] = weight` 로 표현한다.

```js
const graph = [
  [0, 1, 0, 0],
  [1, 0, 1, 1],
  [0, 1, 0, 0],
  [0, 1, 0, 0]
]
```

### Adjacency List (인접 리스트)

인접 리스트는 배열과 연결 리스트로 표현된다. 배열의 인덱스는 노드를 나타내고, 배열의 값은 해당 노드와 연결된 노드들의 연결 리스트를 나타낸다.

```js
const graph = {
  0: [1],
  1: [0, 2, 3],
  2: [1],
  3: [1]
}
```
[Javascript Graph Adjacency List](./graph.js)


