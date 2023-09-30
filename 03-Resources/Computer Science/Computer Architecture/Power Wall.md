tags : #computerarchitecture 

- 현재 컴퓨터 공정에서 Power가 차지하는 위치는?
- Dennard Scaling의 정의와 한계는?

---

![[Pasted image 20230918124712.png]]
위 그림은 `Clock Rate`와 `Power`를 나타낸 그래프이다.
2000년대에 들어, `Clock Rate`를 높이는 것보다 `Power`를 줄이는 것이 관건이 되었다.

##### In CMOS IC technology
$$\text{Power}\propto\text{Capacitive load}\times\text{Voltage}^2\times\text{Frequency}$$
공학자들은 전력을 줄이기 위해 많은 노력을 기울였다. 그 결과, 전압을 $5V$에서 $1V$로 줄이는 성과를 보여주었다. 하지만 여기서 전압을 더 줄이면, $0$과 $1$의 경계가 모호해지는 사태가 발생한다.

$\text{Frequency}$는 무려 약 1000배 증가 하였고, 결과적으로 $\text{Power}$는 약 30배 가까이나 증가했다.
$\text{Capacitive load}$는 `용량성 부하`이다. `Area of Curcuit`과 비례한다. 크게 중요한 개념은 아니다.

여기서 더 많은 `Heat`와 `Voltage`를 더 줄일 수 없다.
그럼 [[Performence]]를 높이기 위해 어떻게 해야할까?

##### Dennard Scaling
트랜지스터의 크기가 꾸준히 작아지고 이에 가하는 전압도 줄어들지만, 트랜지스터의 Frequency(속도)와 면적 당 개수(밀도)도 증가하며 **최종적으로 Power의 밀도는 꾸준히 유지**된다는 것이다.

* Dynamic Power
$$P_{dyn}=\alpha C{V_{dd}}^2f$$
$\alpha$는 게이트 스위치가 변할 때 클럭 사이클의 비율이다 (최대 $1/2$)
$C$와 $V_{dd}$는 $1/S$와 비례한다.
$f$는 $S$와 비례한다.
따라서 $P_{dyn}$은 $1/S^2$와 비례한다.

하지만, 기술의 발전에 따라 단위 영역 당 트랜지스터 개수는 $S^2$씩 증가한다.

즉, 최종적으로 Power의 밀도는 유지된다.

* End of Dennard Scaling
트랜지스터의 면적을 줄이는 것이 기술적인 한계에 봉착했다.

##### Summary
- 최근, `Clock Rate`를 높이는 것보다 `Power`를 줄이는 것이 관건이 되었다.
- Dennard Scaling은 **최종적으로 Power의 밀도는 꾸준히 유지**된다는 것이다.
- 트랜지스터의 면적을 더 이상 줄이기 어려워 한계에 봉착했다.