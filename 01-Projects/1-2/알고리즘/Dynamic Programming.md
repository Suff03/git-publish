tags : #algorithm 

- Dynamic Programming이란?
- Dynamic Programming을 사용하기 위한 두 가지 조건은?
- Dynamic Programming에서 자주 활용되는 메서드는?
- Assembly Line Scheduling의 Solution
---

##### Dynamic Programming
**Dynamic Programming**은 문제를 여러 하위 문제로 나누어 문제를 해결하는 방법이다. 이때, 한 번 푼 하위 문제는 다시 풀지 않는다.

##### Requirements
Dynamic Programming을 사용하기 위해서는 두 가지 조건을 만족해야 한다.

* ==Overlapping Subproblems(중복 하위 문제)==
	여러 하위 문제로 나누는 과정에서 중복 하위 문제가 생긴다.

* ==Optimal Substructure(최적 부분 구조)==
	문제에 대한 최적 해결 방법은 부분 문제의 최적 해결 방법의 합이다.


##### Methods
Top-Down, Bottom-Up 방식 중에서 Dynamic Programming은 `Bottom-up`이 효율이 좋다.

* Top-Down : 재귀
* Bottom-Up : 반복문

##### Solvable Problem
[[Assembly Line Scheduling]]
[[Matrix Chain Multiplication]]
[[Knapsack Problem]]