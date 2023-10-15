tags : #probability 
- 감마 함수의 정의
- 감마 함수의 성질
- 감마 분포의 정의와 식, 통계값
---
감마 분포는 [[Normal Distribution]]으로 설명할 수 없는 부분을 보완할 수 있다.

##### Gamma Function
팩토리얼 함수는 오로지 자연수만을 정의역으로 가지는 함수이다. 팩토리얼을 복소수까지 확장해 새로운 함수를 만들어 낸 것이 **감마 함수**다.
$$\Gamma \left( \alpha \right) = \int\limits_0^\infty {x^{\alpha - 1} e^{ - x} dx}$$
감마 함수는 다음과 같은 성질을 가진다.
$$\Gamma(\alpha)=(\alpha-1)!$$
$$\Gamma(1)=1$$
$$\Gamma(\frac{1}{2})=\sqrt{\pi}$$

##### Gamma Distribution
$\alpha$번째 사건이 일어날 때 까지 걸리는 시간에 대한 연속확률분포를 감마 분포라고 한다. (평균 횟수 : $\beta$)
$$
f(x ; \alpha, \beta)= \begin{cases}\frac{1}{\beta^\alpha\Gamma(\alpha)}x^{\alpha-1}e^{\frac{-x}{\beta}}, & x>0, \\ 0, & \text { elsewhere, }\end{cases}
$$

감마 분포의 평균과 분산은,
$$\begin{align*}
&\mu=\alpha\beta\\
&\sigma^2=\alpha\beta^2
\end{align*}$$
