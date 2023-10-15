tags : #algorithm 

---
##### Activity Selection Problem
$n$개의 활동이 있다. 여러 Activity들의 정보를 보고 **겹치지 않고**, **최대**로 많이 활동을 하기 위한 방법을 어떻게 구할까?

##### Solution
[[Greedy Algorithm]]을 이용하여 쉽게 해결이 가능하다.

시작 시간 $s_i$와 종료 시간 $f_i$가 주어졌다고 가정하자.
종료 시간이 오름차순으로 정렬 돼있다면,
![[Pasted image 20231007195306.png]]
![[Pasted image 20231007195259.png]]

여기서, 현재 시각을 기준으로 **가장 빨리 끝나는 활동**만을 계속한다.
그럼 우리가 선택할 수 있는 최적의 활동은 $\{a_1,a_3,a_6,a_8\}$이다.

##### Optimal Substructure
먼저, `Optimal Substructure`임을 증명하자.
$S_{ij}=\{{a_{k}}\mid f_{i}\leq s_k<f_{k}\leq s_j\}$이다. $S_{ij}$는 공집합이 아니며, 최소한 한 개의 활동이 존재한다.

예를 들면,
![[Drawing 2023-10-08 23.06.36.excalidraw|600]]
$S_{14}=\{a_3\}$이다.

일반화 하면,
![[Drawing 2023-10-08 23.09.58.excalidraw|600]]

**Claim** $A_{ij}=\{a_{k}\cup A_{ik} \cup A_{kj}\}$ 여기서 $A_{ij}$는 $S_{ij}$의 최적의 해이다.

![[Drawing 2023-10-08 23.14.10.excalidraw|600]]

만약 아니라면?
1. $A_{ij}$는 $S_{ij}$의 최적의 해가 아니다.
2. "$A_{ik}$는 $S_{ik}$의 최적의 해이면서, $A_{kj}$는 $S_{kj}$의 최적의 해이다."가 아니다.

이는 **모순**이다. 
"$A_{ik}$는 $S_{ik}$의 최적의 해이면서, $A_{kj}$는 $S_{kj}$의 최적의 해이다."의 부정은 "$A_{ik}$는 $S_{ik}$의 최적의 해가 아니거나, $A_{kj}$는 $S_{kj}$의 최적의 해가 아니다."이다.

여기서 세 가지 가능성이 존재한다. 그리고 세 가지 가능성 모두 **모순**이다.

한 가지만 보자면,
- $A_{ij}$는 $S_{ij}$의 최적의 해이다.
- $A_{ik}$는 $S_{ik}$의 최적의 해가 아니다.
- $A_{kj}$는 $S_{kj}$의 최적의 해이다.

이는 $A_{ij}$가 $S_{ij}$의 최적에 해라는 것에 모순이다.

따라서 이는 `Optimal Substructure`이다.

최적 부분 구조 문제는 `bottom-up` 방법을 이용해 해결이 가능하다. 하지만, 이 문제는 `greedy choice property`로 방법을 이용해 쉽게 풀 수 있다.

##### Greedy Choice Property
최적의 해결 방법이 있다고 가정하자. 공집합이 아닌 부분 문제 $S_{ij}$가 있다. 그리고 $a_m$을 가장 빨리 끝나는 활동이라고 하자.
$$f_m=\min\{f_k:a_{k}\in S_{ij}\}$$
여기서,
1. $a_m$은 최적의 해결 방법에 포함된다.
2. 하위 문제 $S_{im}$은 공집합이다. 따라서, $S_{mj}$만 고려한다.

첫 번째 "$a_m$은 최적의 해결 방법에 포함된다."를 보자.

만약 포함이 된다면 증명된 것이다. 그럼, $a_m$이 최적의 해의 구성이 아니라고 가정하자.
$A=\{x,\cdots\}$, $B=\{a_m,\cdots\}$ 

여기서, $x$를 $a_m$으로 대체하여도 상관이 없다. 현 상황에서 선택 할 수 있는 가장 빠른 경우를 선택하지 않아도, 가장 빠른 경우로 대체가 가능하다. 대체 해도 할 수 있는 활동의 수는 일정하기 때문이다. 

따라서, 종료가 빠른 상황만 선택하면 최적의 해가 된다.

두 번째 "하위 문제 $S_{im}$은 공집합이다. 따라서, $S_{mj}$만 고려한다."를 보자.

만약 아닐 시,
![[Drawing 2023-10-08 23.37.28.excalidraw|600]]
이는 **모순**이다. $a_m$이 현 상황에서 선택할 수 있는 가장 빨리 끝나는 활동이기 때문이다.

따라서, $S_{mj}$만 고려해도 된다. 부분 문제의 크기가 2에서 1로 줄었다.

##### Recursive Activity Selector
```python
Recursive-Activity-Selector(s, f, i, n)
	m <- i + 1
	while m <= n and s[m] < f[i] # Find the first activity in S_{i,n+1}
		do m <- m + 1 # i의 종료 시간보다 늦게 시작하는 작업 찾을 때까지 순회
	if m <= n
		then return {a[m]} ∪ Recursive-Activity-Selector(s, f, m, n)
		else return ∅
```

![[phpArQlqe.jpg]]

**Ex)**

![[Drawing 2023-10-09 14.38.32.excalidraw|600]]

$\text{R-A-S}(s,f,0,6)$ 이라고 하자. $i$는 $0$부터 시작하므로,
첫 번째 순회
$$\begin{align*}
&m=1\\
&s_1<f_{0}\text{ (X)}\\
&\{a_1\}\cup\text{R-A-S}(s,f,1,6)
\end{align*}$$
두 번째 순회
$$\begin{align*}
&m=2\\
&s_2<f_{1}\text{ (X)}\\
&\{a_2\}\cup\text{R-A-S}(s,f,2,6)
\end{align*}$$
세 번째 순회
$$\begin{align*}
&m=3\\
&s_3<f_{2}\text{ (O)}\\
&s_4<f_{2}\text{ (X)}\\
&\{a_4\}\cup\text{R-A-S}(s,f,4,6)
\end{align*}$$
...

시간 복잡도는 $\mathcal{O}(n)$
