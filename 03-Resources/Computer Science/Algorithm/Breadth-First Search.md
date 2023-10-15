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

##### Breadth-First Search
```python
BFS(G, s)
for each vertex u ∈ V[G] - {s}
	color[u] <- WHITE
	d[u] <- ∞
	π[u] <- NIL
	
color[s] <- GRAY
d[s] <- 0
π[s] <- NIL
Q <- ∅
ENQUEUE(Q, s)

while Q ≠ ∅
	u = DEQUEUE(Q)
	for each v ∈ Adj[u]
		if color[v] == WHITE
			color[v] <- GRAY
			d[v] <- d[u] + 1
			π[v] <- u
			ENQUEUE(Q, v)
	color[u] <- BLACK
```

1. s를 제외한 모든 정점의 color를 white, 거리를 무한대, 선행자를 NIL로 초기화
2. 시작 정점 s의 색깔을 gray, 거리를 0, 선행자를 NIL로 설정. 그리고 Q에 s를 대입
3. Q가 비어있을 때까지 반복. 매 시행마다 Q에서 정점을 하나씩 deque. 정점에 대해 모든 인접한 정점을 방문할 예정이다. (이전 u, 현재 인접 정점 v) 만약 인접한 정점이 White면 Gray로 바꾼 후, 거리를 이전 거리의 거리 + 1을 하고, 선행자를 u로 변경한다. 그 후, 현재 검사중인 v를 Q에 넣는다. Q가 White가 아니면 아무일도 일어나지 않고 다음 인접 정점을 검사한다. 모든 인접 정점을 확인했다면, u는 더 이상 방문할 정점이 없으므로 Black으로 변경된다.

##### Time Complexity
처음 for문 : $\vert V\vert-1$
while 문 : 최대 $\vert V\vert$
for each v ∈ G.Adj : 최대 $\vert E\vert$
따라서, 총 시간 복잡도는 $\mathcal{O}(\vert V\vert+\vert E\vert)$
