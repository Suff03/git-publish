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

##### Assembly Line Scheduling Problem
![[Pasted image 20230926213116.png]]
- 원은 `Time Cost`를 의미한다.
- 생산 라인을 옮길 시, 추가 비용이 발생한다.
- 목표는 <u>가장 빠른 생산 루트</u>를 찾는 것이다.

Optimal Substructure Property
![[Drawing 2023-09-26 21.08.23.excalidraw|650]]
$A$를 $a$에서의 최적의 해, $B$를 b에서의 최적의 해 + $t$(transfer cost)라고 할때,

$x$에서의 최적의 해(가장 저렴한 가격)는
$$\min(A, B)+y$$
이다.

<u>만약 아니라면?</u>

$A<B, A>B, A=B)$ $min(A, B) + y$보다 더 나은 해가 존재한다.
하지만, A

여기 모르겠음..

*Solution 1)*
Brute-force 알고리즘을 이용한 풀이.
매 번마다 모든 가능한 수에 대해 계산한다. 시간 복잡도는 $\Omega(2^n)$.

*Solution 2)*
동적 계획법을 이용한 풀이.
![[Pasted image 20230926213116.png]]
![[Pasted image 20230926213048.png]]

![[Drawing 2023-09-26 21.37.33.excalidraw|650]]

$A$를 $y$의 최적의 해, $B$를 $z$에서의 최적의 해 + $t$(transfer cost)라고 할때,

$x$에서의 최적의 해(가장 저렴한 가격)는
$$\min(A, B)+a$$

$C$를 $z$의 최적의 해, $B$를 $y$에서의 최적의 해 + $s$(transfer cost)라고 할때,

$w$에서의 최적의 해(가장 저렴한 가격)는
$$\min(C, D)+b$$

$\min(A, B)+a$를 1번 테이블에, $\min(C, D)+b$를 2번 테이블에 계속해서 쌓아나간 다음, exit에 도달할 때 $\min(x + x_{1}, y+ x_2)$를 계산한다.

따라서, 시간 복잡도는 $\mathcal{O}(n)$이다.

##### Summary