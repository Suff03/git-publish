tags : #algorithm 
- 연결 요소의 의미
- 연결 요소의 의사 코드
- 연결 요소 시간 복잡도
---
##### Connected Component
[![](https://i.imgur.com/EK3sI5c.png "source: imgur.com")](https://imgur.com/EK3sI5c)
원래의 그래프 $G$ 가운데, Node와 Edge가 서로 겹치지 않는 Subgraph $G'$이되, $G'$ 내에서 모든 `Node` 쌍에 대해 경로가 존재하는 것을 말한다.

위의 그림에서, 연결 요소는 총 4개이다.
[[Disjoint Sets]]을 이용하여, 연결 요소인지 판단할 수 있다.

##### Psuedocode
```python
CONNECTED-COMPONENTS(G)
	for each vertex v in V[G]
		do MAKE-SET(v)
	for each edge (u. v) in E[G]
		do if FIND-SET(u) ≠ FIND-SET(v)
			then UNION(u, v)
```

##### Time Complexity
MAKE-SET 횟수 : V(NODE)의 개수
FIND-SET + UNION 횟수 : E(EDGE)의 개수

$\mathcal{O}((V+E)\alpha(V))$