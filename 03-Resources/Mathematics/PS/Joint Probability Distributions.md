##### Joint Probability Distribution

두 개 이상의 확률변수를 고려한다. 

$X$와 $Y$가 두 이산형 확률변수라 할 때, 두 변수의 확률분포는 확률변수 $X$와 $Y$의 범위 내에서 어떤 $(x,y)$에 대하여 $f(x,y)$를 값으로 가지는 함수로 표시될 수 있다.

이를 $X$와 $Y$의 **결합확률분포**라한다.

$$f(x,y)=P(X=x,Y=y)$$
즉, $f(x,y)$는 $x$, $y$가 <u>동시에 일어날 확률</u>이 된다.

##### Requires
다음 조건이 만족될 때 함수 $f(x,y)$를 이산형 확률변수 $X$와 $Y$의 **결합확률분포** 또는 **결합확률질량함수**라 한다.

$$
\begin{align*}
&1.f(x,y)\geq 0, \text{for all }(x,y)
\\&2.\sum_{x}^{}\sum_{y}^{}f(x,y)=1
\\&3.P(X=x,Y=y)=f(x,y)
\end{align*}
$$
$x, y$ 평면상의 어떤 영역 $A$에 대해 $P[(X, Y) \in A]=\sum\sum_{A}^{}f(x,y)$가 된다.


##### Joint Density Function
$X$와 $Y$가 연속형 확률변수라 할 때, **결합밀도함수** $f(x,y)$는 $xy$평면 위에 놓여 있는 표면이 되며, $A$를 $xy$평면상의 임의의 영역이라면 $P(X, Y)\in A$는 밑면 $A$와 표면으로 구성되는 입체의 부피와 같게 된다.

$$
\begin{align*}
&1.f(x,y)\geq 0, \text{for all }(x,y)
\\&2.\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}f(x,y)dxdy=1
\\&3.P[(X, Y)\in A]=\int \int _Af(x,y)dxdy, \text{for any region }A \text{ in the } xy \text{ plane.}
\end{align*}
$$

##### Marginal Distribution
$X$와 $Y$의 **주변분포**는 다음과 같이 주어진다.

이산형인 경우,
$$g(x)=\sum_{y}f(x,y), h(y)=\sum_{x}f(x,y)$$

연속형인 경우,
$$g(x)=\int_{-\infty}^{\infty}f(x,y)dy,h(y)=\int_{-\infty}^{\infty}f(x,y)dx$$

##### Conditional Distribution
$X=x$로 주어졌을 때 확률변수 $Y$의 **조건부 분포**는 다음과 같이 주어진다.
$$f(y\mid x)=\frac{f(x,y)}{g(x)}, g(x)>0$$

같은 방법으로 $Y=y$로 주어졌을 때 확률변수 $X$의 조건부 분포는,
$$f(x\mid y)=\frac{f(x,y)}{h(y)},h(y)>0$$

