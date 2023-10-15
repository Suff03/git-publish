tags : #probability 
- 정규분포 식
- 정규분포의 7가지 성질
- 표준정규분포
- 이항분포의 정규근사
---
##### Normal Distribution
평균 $\mu$와 분산 $\sigma^2$를 가지는 정규확률변수 $X$의 확률분포는,
$$X \sim \mathcal{N}(\mu,\,\sigma^{2})=\frac{1}{\sqrt{2 \pi} \sigma} e^{-\frac{1}{2 \sigma^2}(x-\mu)^2}, \quad-\infty<x<\infty$$
와 같이 주어진다.

##### Following Properties
![수학 공식 | 고등학교 > 정규분포의 뜻과 성질 – MATH FACTORY](https://www.mathfactory.net/wp-content/uploads/%EC%88%98%ED%95%99-%EA%B3%B5%EC%8B%9D-%EC%A0%95%EA%B7%9C%EB%B6%84%ED%8F%AC-02.png)
1. $x=\mu$에서 곡선이 ==최댓값==이자 ==최빈값==이다.
2. 곡선은 $\mu$에 대해 대칭이다.
3. $\mu+\sigma$에서 변곡점을 가진다.
4. $\mu$에서 멀어질수록 정규곡선은 수평축에 접근한다. (점근선을 가진다.)
5. 곡선과 $x$축 사이의 면적은 **총 1**이다.
6. $\sigma$가 같다는 가정 하에, $\mu$가 **클 수록** 곡선의 모양 변화 없이 오른쪽으로 이동한다.
7. $\mu$이 같다는 가정 하에, $\sigma$가 **클 수록** 더 낮고 넓게 퍼진다.


##### Standard Normal Distribution
정규밀도함수의 적분의 어려움을 피하고, 쉽게 이용하기 위해 치환을 이용한다.

서로 다른 정규분포를 따르는 자료들의 객관적인 비교와, 표준정규분포표를 이용하여 확률을 구하기 위해 만들어진 개념이다.

모든 정규확률변수 $X$를 평균이 $0$이고 분산이 $1$인 정규확률변수 $Z$로 치환시킬 수 있다.
$$Z=\frac{X-\mu}{\sigma}$$
평균이 $0$이고, 분산이 $1$인 정규확률변수의 분포를 **표준정규분포**라고 한다.

##### Normal Approximation to the Binomial
![Approximating a Binomial Distribution with a Normal Curve](https://math.oxford.emory.edu/site/math117/normalApproxToBinomial/normal_approx_to_binomial.png)
$n$이 충분히 크게 되면, [[Binomial Distribution]]을 정규분포로 근사할 수 있다.

확률변수 $X$가 이항분포를 따르고, $n$이 충분히 클 때, $X$는 근사적으로 정규분포 $X \sim \mathcal{N}(np,npq)$를 따른다. 표준정규분포로 근사하면,
$$Z=\frac{X-np}{\sqrt{npq}}$$
따라서, $Z \sim \mathcal{N}(0,1)$이다.
