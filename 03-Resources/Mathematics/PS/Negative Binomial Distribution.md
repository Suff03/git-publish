tags : #probability 
- 기하분포의 확률변수 $X$의 의미
- 기하분포의 식과 통계량
- 음이항분포의 확률변수 $X$의 의미
- 음이항분포의 식과 통계량
---
##### Geometric Distribution
첫 번째 성공이 일어날 때까지 필요한 시행횟수 $X$의 확률분포. 음이항분포의 특수한 경우로 k=1인 경우와 같다.
![[Drawing 2023-10-03 17.41.18.excalidraw|600]]

$$g(x;p)=(1-p)^{x-1}p$$

기하분포의 평균과 분산은,
$$\begin{align*}
&\mu=\frac{1}{p}\\
&\sigma^2=\frac{(1-p)}{p^{2}}
\end{align*}$$

##### Negative Binomial Distribution
고정된 $n$번의 실험에서 $x$번의 성공이 일어날 확률의 분포인 [[Binomial Distribution]]대신 $k$번째 성공이 $x$번째 시행에서 일어날 확률의 분포를 음이항분포라 한다.

![[Drawing 2023-10-03 17.46.24.excalidraw|600]]

음이항실험에서 $k$번째 성공이 일어날 때까지의 시행횟수 $X$를 **음이항확률변수**라고 한다. 이 이산형 확률분포를 음이항분포라 한다. $k$번째 성공이 일어날 때까지 최소한 $k$번은 시행해야 하므로 $X=k,k+1,k+2,...$

독립적인 반복시행에서 성공확률이 $p$라 하면 $k$번째 성공이 일어날 때까지의 시행횟수인 확률변수 $X$의 확률분포는
$$b^*(x;k,p)={x-1\choose k-1}p^k(1-p)^{x-k}$$

음이항분포의 평균과 분산은,
$$\begin{align*}
&\mu=\frac{r}{p}\\
&\sigma^2=\frac{r(1-p)}{p^{2}}
\end{align*}$$
