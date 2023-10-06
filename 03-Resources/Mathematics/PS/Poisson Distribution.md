tags : #probability 
- 포아송 분포가 활용되는 경우
- 포아송 분포의 확률변수 $X$의 의미
- 포아송 분포의 식과 기댓값, 분산
- 이항분포의 포아송 분포 근사
---
수많은 사건 중, $(n\rightarrow\infty)$ **특정한 사건이 발생할 확률이 매우 작을 때** $(p\rightarrow 0)$ 사용하는 분포이다. 현대에는 계산 기술이 발달해서 잘 쓰이진 않는다.

일정한 시간간격 $t$ 동안에 특정 사건이 발생하는 결과의 수를 나타내는 포아송 확률변수 $X$의 확률분포는,
$$p(x;\lambda t)=\frac{e^{-\lambda t}(\lambda t)^x}{x!}$$

여기서 $\lambda$는 단위시간에서 발생하는 **결과의 평균수**이다. 문제를 풀 때 단위시간을 유의해야 한다.

포아송 분포의 평균과 분산은,
$$\begin{align*}
&\mu=\lambda t\\
&\sigma^2=\lambda t
\end{align*}$$
##### Poisson Approximation to Binomial
$(n\rightarrow\infty)$, $(p\rightarrow 0)$일 때, 이항분포를 포아송 분포로 근사시킬 수 있다.\
$$b(x;n,p)\xrightarrow[]{n\rightarrow\infty}p(x;\mu)$$

$\lambda$에 이항분포의 평균 $np$를 대입한다.
