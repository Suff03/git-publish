<h5>Conditional Provability</h5>
표본공간 $S$의 두  사건 $A$, $B$에 대하여 확률이 0이 아닌 사건 $A$가 일어났을 떄 사건 $B$가 일어날 확률을 사건 $A$가 일어났을 때의 사건 $B$의 **조건부확률**이라 한다.
$$P(B \mid A)=\frac{P(A\cap B)}{P(A)}, P(A)>0$$

$A$와 $B$가 독립이라면,
$$P(A \mid B)=P(A)$$

조건부확률은 축소된 표본공간에서의 확률이다. $P(A \mid B)$는 사건 $A$를 새로운 표본공간으로 생각하고 표본공간인 사건 $A$에서 사건 $A\cap B$가 일어날 확률을 의미한다.

$P(B'\mid A)$는 사건 $A$를 표본 공간으로 생각했을 때 사건 $B$의 여사건의 확률이므로,
$$P(B'\mid A)=1-P(B\mid A)$$

<h5>Mutually Exclusive vs Independence vs Dependence</h5>
* Mutually Exclusive : $A$와 $B$는 동시에 일어나지 않음.
$$P(A\cup B)=P(A)+P(B)$$

* Independence : $A$와 $B$가 각각 일어나든지 안 일어나든지 간에 상관없이 서로 영향을 주지 않음.
$$P(A\cap B)=P(A)P(B)$$

* Dependence : $A$와 $B$가 서로 영향을 줌.
$$P(A\cap B)=P(A)P(B\mid A)=P(B)P(A\mid B)$$
<h5>Multiplicative Rule</h5>
순열을 생각하면 된다.
If in an experiment the events $A$ and $B$ can both occur, then
$$P(A\cap B) = P(A)P(B \mid A), P(A)>0$$ 
두 사건이 독립일시,
$$P(A\cap B)=P(A)P(B)$$

If in an experiment the events $A_1,A_2,...,A_k$ can occur, then
$$P(A_1\cap A_2\cap\cdots\cap A_k) = P(A_1)P(A_2 \mid A_1)P(A_{3}\mid A_{1}\cap A_{2})\cdots P(A_{k}\mid A_1\cap A_2\cap\cdots\cap A_k)$$

$A_1,A_2,...,A_k$가 모두 서로 독립이라면,
$$P(A_1\cap A_2\cap\cdots\cap A_k) = P(A_1)P(A_{2})\cdots P(A_k)$$