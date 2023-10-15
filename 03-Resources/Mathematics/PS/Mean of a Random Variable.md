tags : #probability 

---
##### Mathematical Expectation
확률변수를 하나로 요약하는 수, 평균을 수학적 기댓값이라고 한다.

이산형
$$\mu=E(X)=\sum_{x}xf(x)$$

연속형
$$\mu=E(x)=\int_{-\infty}^{\infty}xf(x)\ dx$$

산술평균은 모든 값이 동일하게 나올 가정을 토대로 한 특수한 꼴의 기댓값이라고 말할 수 있다. 따라서 기댓값을 가중평균이라고도 한다.

확률변수의 함수에 대한 기댓값도 나타낼 수 있다.
$$\mu_{g(X)}=E[g(X)]=\sum_{x}g(x)f(x)$$$$\mu_{g(X)}=E[g(X)]=\int_{-\infty}^{\infty}g(x)f(x)\ dx$$
##### Linearity
이산형, 연속형 확률변수인 경우 모두 다음과 같은 성질들이 성립한다.
$$E(aX+b)=aE(X)+b$$
$$E(b)=b$$
$$E(cX)=cE(X)$$
$$E[g(X)±h(x)]=E[g(x)]±E[h(x)]$$

##### Joint Probability Distribution
$$
\mu_{g(X, Y)}=E[g(X, Y)]=\sum_x \sum_y g(x, y) f(x, y)
$$
$$
\mu_{g(X, Y)}=E[g(X, Y)]=\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(x, y) f(x, y)\ dxdy
$$

$X$와 $Y$가 독립이면,
$E[g(x)h(y)]=E[g(x)]E[h(y)]$

$X$의 주변 분포 $g(x)$에 대해서도 다음이 성립한다.
$$
E(X)= \begin{cases}\sum_x \sum_y x f(x, y)=\sum_x x g(x) & \text { (discrete case) } \\ \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} x f(x, y) d y d x=\int_{-\infty}^{\infty} x g(x) d x & \text { (continuous case) }\end{cases}
$$

