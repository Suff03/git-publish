tags : #algorithm #probability

* The Hiring Problem의 전개 과정은?
* The Hiring Problem의 평균 비용은?
* Probility Analysis란?
* Randomized Algorithm이란?

---

`Probabilistic Analysis`를 이용하여 `The Hiring Problem`을 분석한다.

##### The Hiring Problem
*Scenario*
* 고용 업체를 이용해 신입 사원을 채용하고 있다.
* 업체는 당신에게 하루에 한 명씩 후보자를 보낸다.
* 지원자의 면접을 본 다음 바로 채용 여부를 결정해야 한다. 만약 당신이 고용한다면, 현재 채용된 직원을 해고해야 한다. (비록 방금 전에 고용됐던 사람이라도 해고해야 한다.)
* 인터뷰에서 후보자당 $C_i$의 비용이 든다. (인터뷰 비용은 업체에게 주어진다.)
* 고용 비용은 후보자당 $C_h$의 비용이 든다. (업체에게 줄 고용 비용 + 직원을 해고하는 비용)
* Assume that $C_h>C_i$ .
* 당신은 매번 인터뷰를 하면서 최고의 후보자를 채용하는 데 전념하고 있다. 즉,<u> 더 나은 후보자를 찾을 때마다 채용되어 현재 일하고 있는 직원을 해고해야 한다.</u> 항상 누군가를 고용하고 있어야 하기 때문에 면접을 보는 첫 번째 후보자를 고용한다. 

*Goal* : 이 전략의 총 비용이 얼마일지 결정해라.

```python
HIRE-ASSISTANT(n)
	best <- 0 # candidate 0 is a least-qualiÞed dummy candidate
	for i <- 1 to n
		do interview candidate i
			if candidate i is better than candidate best
				then best <- i
					hire candidate i
```

*Cost* : 만약 $n$명의 후보자가 있고 그 중 $m$명을 고용했다면, 총 비용은 $\mathcal{O}(nC_{i}+mC_h)$이다.
* 얼마나 많은 후보자를 고용했든, 인터뷰 비용으로 $nC_i$를 지불해야 한다.
* 그러므로 $mC_i$ 분석에 집중해야 한다.
* $mC_i$ 는 **후보자 인터뷰 순서**에 영향을 받는다

##### Worst Analysis
 $n$명 모두를 인터뷰 하는 경우이다.
 즉, $\mathcal{O}(nC_{i}+nC_h)={O}(nC_{h})$이다. ($C_h>C_i$로 가정했으므로)

##### Probability Analysis
일반적으로, 우리는 후보의 순서를 알 수 없다. 후보자가 랜덤의 순서로 들어온다고 가정한다.
확률적 분석은 주어지는 `Input`이 어떠한 확률 분포를 가진다는 가정 아래에서 이루어진다.

##### Randomized Algorithm
대부분의 경우 Input의 확률 분포를 알기 어렵다. 대신, Input에 분포를 부여하기 위하여 알고리즘의 일부분에 Randomization을 사용한다.

무작위 알고리즘의 수행 시간을 분석할 때는 분포에 대한 기댓값을 취해 기대 수행 시간을 계산한다.

*Change the scenario
* 고용 업체는 $n$명의 후보자 명단을 미리 보내준다.
* 매일, 인터뷰할 후보자를 랜덤하게 고른다. (아직 인터뷰 하지 않은 사람에 한해서)
* 후보자들이 무작위로 제시되는 대신, 과정을 통제하고 랜덤 순서를 강화한다.

그럼, The Hiring Problem의 평균적인 비용 함수를 어떻게 계산할 수 있을까?

##### Time Complexity
먼저 `Indicator Random Variable`을 정의한다.
$$I\{A\}= \begin{cases}
1 & \text{if A occurs ,}  \\
0 & \text{if A does not occur.}  
\end{cases}$$

발생하면 $1$, 발생하지 않으면 $0$을 출력하는 함수다.
그 다음, $X_A=I_A$라 하자.
$$E(X_A)=1\times P(A)+0\times P(A')$$

따라서, $E(X_A)=P(A)$를 만족한다.
Random Variable $X$를 새로운 직원이 고용된 횟수로 정의하자. 그리고 Indicator Random Variables $X_1, X_2,...,X_n$을 정의하자. $X_i=I$ ($i$번째 후보자 고용), $X=X_1+ X_2+\cdots+X_n$

$E(X_i)$는 $i$번째 후보자가 고용될 확률과 같다. $E(X_i)=Pr\{\text{candidate } i \text{ is hired}\}$
그러므로, $E(X_i)=\frac{1}{i}$이다. ($i$번째 지원자가 나머지 모든 지원자보다 능력이 있을 확률)

우리의 최종 목표는 $X$의 기댓값을 계산하는 것이다.
$$
\begin{align*}
E(X)&=E(X_1+X_2+\cdots+X_n)\\&=E(X_1)+E(X_2)+\cdots+E(X_n)\\
&=\sum_{i=1}^{n}E(X_i)\\
&=\sum_{i=1}^{n}\frac{1}{i}\\
&=\ln(n)+\mathcal{O}(1)\\
\end{align*}$$

후보가 무작위 순서로 들어올 때, **평균 채용 비용**은 $\mathcal{O}({C_{h}\log}n)$이다.  
