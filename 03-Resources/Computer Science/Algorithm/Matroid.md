#algorithm 

---
##### Matroid
`Matroid`는 다음 조건을 만족하는 순서쌍 $M=(S,I)$이다. ($S$는 유한집합, $I$는 $S$의 부분집합들의 집합이다.)

- Hereditary
$B\in I$ and $A \subseteq B$, then $A\in I$. 이를 $I$의 **상속성**이라고 한다. ($\emptyset\in I$이다.)
즉, 집합 $A$가 $I$에 속하면, $A$의 모든 부분집합은 $I$에 속한다.

- Exchange Property
$A\in I$, $B\in I$, and $\vert A\vert>\vert B\vert$, then $\exists a\leq A-B$ such that $B\cup \{a\}\in I$.
즉, $M$은 교환법칙이 성립한다고 말할 수 있다.
크기가 다른 두 집합 $A$, $B$가 ($\vert A\vert>\vert B\vert$) $I$에 속하면, $B$에는 없고 $A$에 있는 원소 중에서, $B$에 더해서 $I$에 속하게 하는 $A$의 원소 $a$가 존재한다.

**Ex)** $S=\{1,2,3\}$, $I_1=\{\emptyset,\{1\}\}$, $I_2=\{\{1\},\{2\}\}$, $I_3=\{\emptyset,\{1\}, \{2\}, \{3\}, \{1,3\}\}$

- 순서쌍 $(S,I_1)$는 Matroid이다. 모든 조건을 만족하기 때문이다.

- 순서쌍 $(S, I_2)$은 Matroid가 아니다. 공집합이 포함되어 있지 않기 때문이다. (공집합은 모든 집합의 부분집합) `Hereditary`를 만족하지 않는다.

- 순서쌍 $(S,I_3)$는 Matroid가 아니다. `Exchange Property`를 만족하지 않는다.
	$\{1,3\}-\{2\}=\{1,3\}$이다. $\{2\}$에는 없고 $\{1,3\}$에 있는 원소 중에서, $\{2\}$에 더해서 $I$에 속하게 하는 어떤 원소가 존재해야 한다. 즉, $\{1,2\}$가 존재하거나, $\{2,3\}$이 존재해야 한다.

Matroid 구조에서는 [[Greedy Algorithm]]이 최적해를 찾아낼 수 있다. (Greedy Algorithm이 최적해를 찾아낼 수 있는 구조가 모두 Matroid 구조는 아니다.)

##### Graph Matroid
$G(V,E)$가 `Undirected Graph`이면, 그래프 매트로이드 $M_G(S_G,I_G)$는 다음 정의를 따른다.
- $S_G=E$
- 만약 $A$가 $E$의 부분집합이면, $A$가 비순환인 것과 $A\in I_G$임은 동일하다.

**Ex)** 
![[Drawing 2023-10-12 12.18.06.excalidraw|]]
$M_G=(S_G,I_G)$, $S_G=\{1,2,3,4\}$, $I_G=\{\emptyset,\{1\},\{2\},\{3\},\{4\},\{1,2\},\{1,3\},\{1,4\},\{2,3\},\{2,4\},\{3,4\},\{1,3,4\},\{2,3,4\}\}$
$\{1,3,4\}$는 `Cyclic`이므로 $I_G$에 들어갈 수 없다.

##### Task Scheduling Problem
작업 스케쥴링 문제도 `Matroid`를 이용하여 풀 수 있다.
- input
	$S=\{a_1,\cdots,a_n\}$은 $n$개의 단위 시간 작업이다.
	작업에 대한 $n$개의 정수 Deadline $d_1,\cdots,d_n$이 존재한다.
	Deadline에 맞추지 못했을 때의 패널티 $p_1,\cdots,p_n$이 존재한다. (내림차순 가정)

- output
	패널티를 최소로 하는 $S$의 순열을 찾는다.

`Tasking Scheduling Problem`은 `Matroid`이다.
매트로이드는 두 가지 성질을 갖는다. 각각을 확인해보자.

**Hereditary**
$S=\{a_1,a_2,\cdots,a_n\}$이라고 하자. $I$는 ==패널티 없이 스케줄을 마칠 수 있는 활동==들의 부분집합들의 집합이라고 정의한다.

예를 들어,
![[Pasted image 20231012125025.png]]

**Exchange Property**
$N_t(A)$를 $t$ 이하의 시간에 Deadline이 있는 활동들의 개수라고 정의하자.

예를 들어, $A=\{a_1,a_2,a_3\}$, $d_1=2,d_2=1,d_3=3$이라고 할 때,
$N_2(A)=2$, $N_3(A)=3$이다.

$k$를 $N_{t}(x)\leq N_t(y)$을 만족하는 최대 시간이라고 하자. ($k+1$부터는 $N_{t}(x)> N_t(y)$)
$x$는 $y$보다 더 많은 일(deadline : $k+1$)을 포함해야 한다.
$a\in x-y$라고 일 때, (a의 deadline : $k+1$) $\{a\}\cup y\in I$을 만족한다.

```python
Greedy(M, P)
	X <- ∅
	for i <- 1 to n :
		if X ∪ a[i] ∈ I :
			then X <- X ∪ a[i]
	return X
```

![[Pasted image 20231012153327.png]]
![[Pasted image 20231012153639.png]]

시간 복잡도는 $\mathcal{O}(n^2)$이다.
정렬 : $\mathcal{O}(n\log n)$
$X ∪ a_i ∈ I \rightarrow\mathcal{O}(n)$
for loop : $n$번 반복

합계 : $\mathcal{O}(n\log n + n^2)=\mathcal{O}(n^2)$
