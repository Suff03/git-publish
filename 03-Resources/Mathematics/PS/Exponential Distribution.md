tags: #probability 
- 지수 분포의 정의, 식, 통계값
- 지수 분포와 포아송 분포와의 관계
- 지수 분포의 무기억성
---
##### Exponential Distribution
지수 분포는 [[Gamma Distribution]]의 $\alpha=1$일 때의 특수한 경우이다.

첫 번째 사건이 일어날 때 까지 걸리는 시간에 대한 연속확률분포를 지수 분포라고 한다. (평균 횟수 : $\beta$)
$$
f(x ; \beta)= \begin{cases}\frac{1}{\beta}e^{\frac{-x}{\beta}}, & x>0, \\ 0, & \text { elsewhere, }\end{cases}
$$

지수 분포의 평균과 분산은,
$$\begin{align*}
&\mu=\beta\\
&\sigma^2=\beta^2
\end{align*}$$

##### Relationship to the Poisson Process
지수 분포는 [[Poisson Distribution]]과 깊은 관련이 있다.

포아송 분포의 의미는, 구간 $t$당 발생할 횟수의 기댓값이 $\lambda t$인 사건이 $x$회 일어날 확률을 의미한다. $$p(x;\lambda t)=\frac{e^{-\lambda t}(\lambda t)^x}{x!}$$$x=0$ 일 때, $p(0;\lambda t)=e^{-\lambda t}$이다. 이는 구간 $t$당 발생할 횟수의 기댓값이 $\lambda t$인 사건이 $0$회 일어날 확률을 의미한다.

$1-e^{-\lambda t}$는, 구간 $t$당 발생할 횟수의 기댓값이 $\lambda t$인 사건이 **최소한 한 번 이상** 일어날 확률이다.
즉, $t$ 동안 발생할 횟수의 기댓값이 $\lambda t$인 사건이 처음 발생할 때까지의 시간이 $t$보다 작은 경우와 동일하다. 이는, $P(T\leq t)$로 표현할 수 있다. 즉, **누적확률분포**와 동일하다.

누적확률분포를 미분하면 확률밀도함수가 나온다. 따라서, $$P(T=t)=\lambda e^{-\lambda t}$$
구간 $t$동안 발생할 횟수의 기댓값이 $\lambda t$인 사건이 처음 발생할 때까지의 시간이 $t$일 확률
즉, 첫 번째 사건이 일어날 때 까지 걸리는 시간에 대한 확률이다.

##### Memoryless Property
지수 분포는 이전 일을 기억하지 못한다. 다시 말해, 과거의 이력을 망각해버리는 성질이 있다. 무기억성을 가지는 연속형 확률분포는 지수 분포가 유일하다.
$$P(X\geq {t_{0}+t} \mid X\geq t_0)$$
