$$\begin{align*} P(A)  &= P[(E\cap A)\cup(E'\cap A)] \\ &= P(E\cap A) + P(E'\cap A) \\ &=P(E)P(A\mid E)+P(E')P(A\mid E')\end{align*} $$
<h5>Theorem of total probability</h5>
If the events $B_1,B_2,...,B_k$ constitute a partition of the sample space $S$
such that ${P(B_i)}\neq0$ for $i=1,2,...,k$ then for any event $A$ of $S$,

$$P(A)=\sum_{i=1}^{k}P(B_{i}\cap A)=\sum_{i=1}^{k}P(B_{i})P(A\mid B_{i})$$

<h5>Baye's Rule</h5>
`Theorem of total probability`를 이용하여,
$$P(B_{r\mid}A)=\frac{P(B_{r}\cap A)}{P(A)}=\frac{P(B_{r}\cap A)}{\sum_{i=1}^{k}P(B_{i}\cap A)}=\frac{{P(B_r)}{P(A\mid B)}}{\sum_{i=1}^{k}P(B_{i})P(A\mid B_{i})}$$
임을 증명할 수 있다.

* 해석
	1. 표본공간 $S$ : 서로소인 $A_1,A_2,...,A_k$의 합집합
	2. $B$는 $S$ 위에서 정의된 사건

$$P(A_k|B)=\frac{P(A_k)P(B\mid A_k)}{P(A_1){P(B\mid {A_{1})}}+P(A_2){P(B\mid {A_2})}+\cdots+P(A_k){P(B\mid {A_k})}}$$
$P({A_{k}\mid}B)$ 사후 확률, $P(A_k)$ 사전 확률, $P(B\mid A_k)$ likelihood