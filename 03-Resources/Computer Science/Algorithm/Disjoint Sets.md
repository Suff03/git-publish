tags : #algorithm #datastructure 
- 서로소 집합의 의미
- 서로소 집합의 세 가지 연산 방법
- 서로소 집합 연산 시간 복잡도
---
##### Disjoint Sets
**서로소 집합**은 공통 원소가 없는 두 집합을 의미한다. 집합은 각각의 대표 원소를 가지고 있다.
서로소 집합 자료구조는 세 가지 연산으로 이루어진다. (`Make-Set`, `Union`, `Find`)

- Make-Set(X) : 유일한 멤버 X가 포함된 집합을 생성. 집합의 대표 원소는 자기 자신이다.
- Union(X, Y) : X가 속한 집합과 Y가 속한 집합을 합친다.
- Find(X) : X가 속한 집합의 대표 번호를 찾는다.

##### Time Complexity
$n$을 `Make-Set`의 연산 횟수(=원소의 개수), $m$을 `Make-Set`, `Union`, `Find`의 연산 횟수(=총 연산 횟수)라고 할 때, $\mathcal{O}(m + n\log n)$이다. 

이는 `Union` 연산 시 자신이 속한 집합의 크기가 최소 두 배 이상 커지므로, 최대 $\log n$번 연산이 가능하기 때문이다. `Union`은 연산마다 $\mathcal{O}(n)$만큼의 시간 복잡도가 필요하다.

더 나아가, $\mathcal{O}(m\alpha(n))$으로 줄일 수 있다.

#####
[[Connected Component]]
