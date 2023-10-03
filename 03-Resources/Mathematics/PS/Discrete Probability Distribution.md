모든 $x$에 대해 순서상 $(x,f(x))$의 집합이 다음 조건을 만족하면 이를 이산형 확률변수 $X$의 **확률함수**, **확률질량함수**, 혹은 **확률분포**라고 한다.

$$
\begin{align*}
&1.f(x)\geq 0
\\&2.\sum_{x}^{}f(x)=1
\\&3.P(X=x)=f(x)
\end{align*}
$$

##### Cummulative Distribution Function

^05a690

모든 실수 $x$에 대한 $F(x)=P(X\leq x)$를 확률변수 $X$에 대한 **누적분포함수**라고 한다.
$$
F(x)=P(X\leq x)=\sum_{t\leq x}^{}f(t), -\infty<x<\infty
$$