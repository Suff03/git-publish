tags : #algorithm 

---
##### 용어
vertex : 정점
edge : 간선
color : 정점에 색깔 부여 -> 방문 상태 확인
	white : 방문된 적 x
	gray : 방문은 되었지만, 인접한 정점 중에 white 존재 (더 탐색 가능)
	black : 더이상 탐색 불가 (인접한 정점 중 white X)
선행자($\pi$) : 부모 정점
d : 정점까지의 거리
queue : 회색 정점의 집합 관리
back tracking : 더 나아갈 정점이 없으면 다시 부모 정점으로 이동

##### Depth-First Search
```python
DFS(G)
for each vertex u ∈ V[G]
	color[u] <- WHITE
	π[u] <- NIL

time <- 0

for each vertex u ∈ V[G]
	if color[u] == WHITE
		DFS-VISIT(u)
```

```python
DFS-VISIT(u)
color[u] <- GRAY
time <- time + 1
d[u] <- time

for each v ∈ Adj[u]
	if color[v] == WHITE
		π[v] <- u
		DFS-VISIT(v)
color[u] <- BLACK
f[u] <- time <- time + 1
```

DFS
1. 모든 정점의 상태를 white으로, 부모를 NIL로 초기화
2. 그래프의 모든 정점에 대해서 그 정점의 상태가 white면, DFS-VISIT 호출

DFS-VISIT
1. 정점이 처음 방문될 시 시간을 1 증가, GRAY 변경
2. 현재 인접한 모든 정점에 대해 상태가 White면, 부모를 u로 변경, 깊이 있는 탐색을 위해 DFS-VISIT을 재귀 호출
3. 인접한 정점들의 방문이 모두 끝나면 Black으로 변경, 모든 정점을 방문한 시간 기록

##### Time Complexity
DFS
처음 for문 : $\vert V\vert$
다음 for문 : 최대 $\vert V\vert$

DFS-VISIT
for each v ∈ G.Adj : 최대 $\vert E\vert$

따라서, 총 시간 복잡도는 $\mathcal{O}(\vert V\vert+\vert E\vert)$
