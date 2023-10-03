tags : #probability 
- 확률변수란?
- 이산표본공간과 연속표본공간의 차이

---
##### Random Variable
**확률변수**는 표본공간 내에 있는 각 원소에 하나의 실수값을 대응시키는 함수로 정의된다.
주로 대문자 $X$로 나타낸다.

##### Bernoulli Random Variable
$$
 X =
  \begin{cases}
    1     & \text{if $k = 1$}, \\
    0 & \text{if $k = 0$}.
  \end{cases}
$$

두 개의 가능한 값을 $0$과 $1$로 표현

##### Discrete Sample Space
표본공간이 유한개 혹은 셀 수 있는 무한개의 원소로 이루어졌을 때 **이산표본공간**이라 한다.

*Ex)* 확률변수 $X$ : 동전의 앞면이 나온 횟수.
이산표본공간 $\mathcal{\Omega}=\{0, 1, 2, 3\}$(Finite), $\mathcal{\Omega}=\{0, 1, 2, 3,\dots\}$(Countably Infinite) 


확률변수들의 집합이 셀 수 있는 집합이면 그 확률변수를 **이산형 확률변수**(discrete random variable)라 한다.

##### Continuous Sample Space
표본공간이 실선의 어떤 구간 내의 모든 수를 포함할 때 **연속표본공간**이라 한다.

*Ex)* 확률변수 $Y$ : 특정 사건이 일어날 때까지 걸리는 시간.
연속표본공간 : $\mathcal{\Omega}=\{Y>0\}$

확률변수가 연속적인 구간 내의 값을 취하면 **연속형 확률변수**(continuous random variable)라 한다.
