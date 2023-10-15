tags : #algorithm #datastructure 
- 그래프를 구현하는 두 가지 방법
---
##### Graph
그래프는, 정점(Vertex)과 간선(Edge)들의 집합으로 구성된 자료구조이다.

수학적으로 그래프를 표기하는 방법은,
$$G(V,E)$$

##### Types of Graph
- Undirected Graph
	두 정점을 연결하는 간선에 방향이 없는 경우.

- Directed Graph
	두 정점을 연결하는 간선에 방향이 있는 경우, 간선의 방향으로만 이동할 수 있음

- Weighted Graph
	간선에 `cost` 또는 `weight`가 할당된 그래프.

- Complete Graph
	모든 정점 간에 간선이 존재하는 그래프.

##### Graph Implementation
그래프를 구현하는 방식은 크게 두 가지로 나누어진다.
- Adjacency Matrix (인접 행렬)
	그래프의 정점을 2차원 배열로 만든 것이다.
	무방향 그래프일 때는 대칭 형태로 나타난다.
	![img.png](https://blog.kakaocdn.net/dn/wDk4i/btq9HKAolbt/4PFx8ukFyqfr2KaK2sYd00/img.png)

- Adjacency Lists (인접 리스트)
	인접한 정점을 `Linked List`로 저장하는 방법이다.
	![](https://blog.kakaocdn.net/dn/UD8D3/btq9Dm8bq3x/KWSCJ1o7Js9Es0mn0Seko1/img.png)

