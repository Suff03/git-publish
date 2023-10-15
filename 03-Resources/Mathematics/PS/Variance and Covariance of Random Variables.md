tags : #probability 
- 분산의 이산형, 연속형에서의 식, 쉬운 계산법
- 공분산의 이산형, 연속형에서의 식, 쉬운 계산법
- 공분산의 의미 (양, 음, 0)
- 상관계수의 의미
---
##### Variance
평균값만으로 분포의 형태를 설명할 수 없다. 분포의 산포도 고려해야 할 필요가 있다.

이산형
$$\sigma^2=E[(X-\mu)^2]=\sum_{x}(x-\mu)^2f(x)$$

연속형
$$\sigma^2=E[(X-\mu)^2]=\int_{-\infty}^{\infty}(x-\mu)^{2}f(x)dx$$

분산을 쉽게 계산하는 방법은,
$$\sigma^2=E(X^2)-\mu^2$$

##### Covariance
공분산은 두 확률변수 간의 관련성의 척도이다. 두 데이터 관의 관계를 나타낸다.
$$
\sigma_{XY}=E[(X-\mu_X)(Y-\mu_Y)]=\sum_x \sum_y (x-\mu_x)(y-\mu_y) f(x, y)
$$
$$
\sigma_{XY}=E[(X-\mu_X)(Y-\mu_Y)]=\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} (x-\mu_x)(y-\mu_y) f(x, y)\ dxdy
$$

이를 간단히 나타내면, $$\sigma_{XY}=E(XY)-\mu_X\mu_Y$$

공분산의 의미는 다음과 같다.
![[KakaoTalk_20231008_122839023.jpg|600]]

> [!warning] 공분산이 0이면 독립일까?
> $X$와 $Y$가 독립이면 공분산이 0이지만, 역은 아니다.


##### Correlation Coefficient
공분산이 두 확률변수 사이의 관련성을 나타내기는 하지만, 측정 단위에 따라 달라지므로 관련성의 강도를 나타낸다고 말할 수 없다. 상관계수는 측정단위와 무관하게 공분산과 같은 역할을 하는 측도로서 통계학에서 널리 사용된다. **상관 정도의 절대적인 크기**를 말한다.
$$\rho_{XY}=\frac{\sigma_{XY}}{{\sigma_X}{\sigma_Y}}$$

![[Pasted image 20231008123839.png]]
