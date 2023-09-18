`Probabilistic Analysis`를 이용하여 `The Hiring Problem`을 분석한다.

<h5>The Hiring Problem</h5>
*Scenario*
* 고용 업체를 이용해 신입 사원을 채용하고 있다.
* 업체는 당신에게 하루에 한 명씩 후보자를 보낸다.
* 지원자의 면접을 본 다음 바로 채용 여부를 결정해야 한다. 만약 당신이 고용한다면, 현재 채용된 직원을 해고해야 한다. (비록 방금 전에 고용됐던 사람이라도 해고해야 한다.)
* 인터뷰에서 후보자당 $C_i$의 비용이 든다. (인터뷰 비용은 업체에게 주어진다.)
* 고용 비용은 후보자당 $C_h$의 비용이 든다. (업체에게 줄 고용 비용 + 직원을 해고하는 비용)
* Assume that $C_h>C_i$ .
* 당신은 매번 인터뷰를 하면서 최고의 후보자를 채용하는 데 전념하고 있다. 즉, 더 나은 후보자를 찾을 때마다 채용되어 현재 일하고 있는 직원을 해고해야 한다. 항상 누군가를 고용하고 있어야 하기 때문에 면접을 보는 첫 번째 후보자를 고용한다. 

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

<h5>Worst Analysis</h5>
 $n$명 모두를 인터뷰 하는 경우이다.
 즉, $\mathcal{O}(nC_{i}+nC_h)={O}(nC_{i})$이다. ($C_h>C_i$로 가정했으므로)

<h5>Probability Analysis</h5>
후보자가 랜덤의 순서로 들어온다고 가정한다.