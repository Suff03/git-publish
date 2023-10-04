tags : #probability 
- 초기하분포가 활용되는 경우
- 초기하분포의 확률변수 $X$의 의미
- 초기하분포의 식과 기댓값, 분산
---
##### Hypergeometric Distribution
![[Drawing 2023-10-04 08.56.09.excalidraw|500]]

각 시행의 독립이 전제되지 않으며, **비복원추출**의 경우 초기하분포를 활용한다.

$k$개의 **성공**과 $N-k$개의 **실패**로 구성된 크기가 $N$인 유한모집단에서 크기 $n$인 확률표본을 취할 때, 성공의 개수를 나타내는 초기하확률변수 $X$의 확률분포는 다음과 같다.
$$h(x;N,k,p)=\frac{{k\choose x}{N-k\choose n-x}}{N\choose n},\max\{0,n-(N-k)\}\leq x\leq\min\{{m,k}\}$$

초기항분포의 평균과 분산은,
$$\begin{align*}
&\mu=\frac{nk}{N}\\
&\sigma^2={\frac{N-n}{N-1}}{\cdot}n\cdot\frac{k}{N}(1-\frac{k}{N})
\end{align*}$$
