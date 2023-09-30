연속형 확률변수를 취급할 때 $f(x)$를 $X$의 **확률밀도함수**(probability density function) 혹은 간단히 **밀도함수**라고 한다. 연속형 확률변수가 정확히 어느 하나의 값을 가지게 될 확률은 0이다. 따라서, 이산형 확률분포에서처럼 표 형태로 나타낼 수 없다. 임의의 특정한 값이 아닌, <u>구간에 확률을 부여</u>한다.

다음 조건이 만족되면 $f(x)$를 실수의 집합 $R$상에서 정의된 연속형 확률변수에 대한 **확률밀도함수**(pdf)라고 한다.

$$
\begin{align*}
&1.f(x)\geq 0, \text{for all }x\in R
\\&2.\int_{-\infty}^{\infty}f(x)dx=1
\\&3.P(a<X<b)=\int_{a}^{b}f(x)dx
\end{align*}
$$

##### Cummulative Distribution Function
확률밀도함수가 $f(x)$인 연속형 확률변수 $X$의 누적분포함수 $F(x)$는 다음과 같다.
$$
F(x)=P(X\leq x)=\int_{-\infty}^{x}f(x)dt, -\infty<x<\infty
$$

**넓이**라고 생각하자.

정의에 의해 다음의 두 가지 사실을 알 수 있다.
- $P(a<X<b)=F(a)-F(b)$
- 미분이 가능하면, $f(x)=\frac{dF(x)}{dx}$

