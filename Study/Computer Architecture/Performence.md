<h5>Responce Time</h5>
응답 시간. 일을 수행하는 데 얼마나 걸리는가?

<h5>Throughput</h5>
단위 시간 당 총 작업량. 컴퓨터 시스템의 처리 능력을 나타내는 처리량이라고 부른다.
<h5>Define Performance</h5>
`CPU`의 성능은 실행 시간이 적을 수록 늘어난다. 실행 시간을 기준으로 한 성능은 다음과 같다.
$$\text{Performence} = \frac{1}{\text{Excution Time}}$$

따라서, 컴퓨터 $X$와 컴퓨터 $Y$의 성능 비율은 다음과 같이 나타낼 수 있다.
$X$는 $Y$보다 $n$배 더 빠르다.
$$\frac{\text{Performence}_X}{\text{Performence}_Y} = \frac{\text{Excution Time}_Y}{\text{Excution Time}_X}=n$$

<h5>CPU Time</h5>
전반적인 시스템의 시간 측정에는 `Elapsed Time(경과 시간)`이 쓰인다. 이는 `Processing(처리)`, `I/O(입출력)`, `OS overhead(운영체제 처리)`, `Idle time(대기 시간)` 등의 모든 요인을 고려한 총 `Responce Time`이라고 말할 수 있다.

`CPU Time`은 주어진 일을 처리하는 데 걸리는 시간이다. 순수한 `CPU`의 성능에 주목한다. 그러므로 위의 수많은 요소들을 배제한다.

그럼 `CPU Time`은 어떻게 구할까? 우선 [[Clock]] 개념이 필요하다.

<h5>Clock Cycle</h5>
`CPU`가 명령어를 실행하기 위해 데이터를 가져오고, 해석하고, 실행하는 단계이다.
명령어를 실행하는 주기라고 해서 명령 주기라고 부른다.

한 클럭에 걸리는 시간을 `Clock Period`, `Clock Cycle Time`이라 한다.

<h5>Clock Rate</h5>
`CPU`의 초당 클럭 사이클 수를 칭한다. `Clock Frequency`라고도 한다.

내용을 종합하면, `CPU Time`을 다음과 같이 표현할 수 있다.
$$\begin{align*} \text{CPU Time}&= \text{CPU Clock Cycles}\times \text{Clock Cycle Time} \\ &= \frac{\text{CPU Clock Cycles}}{\text{Clock Rate}}\end{align*}$$

성능 향상을 위해선 다음과 같은 일을 수행해야 한다.
* Reducing number of `Clock Cycles`
* Incresing `Clock Rate(Clock Frequency)

하드웨어 디자이너는 `Clock Rate`와 `Cycle Count`의 균형을 맞추어야 할 필요가 있을 것이다.

<h5>CPI</h5>
`CPI(명령어당 클럭 사이클 수)`는 프로그램의 특정 명령어를 수행하는데 소요되는 평균 클럭 사이클 수이다. `CPU`에 의해 결정되며 명령어에 따라 `CPI`가 다르다.

`Clock Cycles(클럭 사이클 수)`는 명령어의 개수와 명령어당 클럭 사이클 수를 곱하여 계산한다.
$$\text{Clock Cycles}=\text{Instruction Count}\times\text{Cycles per Instruction}$$

따라서 `CPU Time`은, 
$$\begin{align*} \text{CPU Time}&= \text{Instruction Count}\times \text{CPI}\times \text{Clock Cycle Time} \\ &= \frac{\text{CPU Clock Cycles}}{\text{Clock Rate}}\end{align*}$$

을 만족한다. 간단히 $\text{CPU Time} =\text{IC}\times \text{CPI}\times \text{Clock Period}$로 표현한다.

[[ISA]]가 같다는 조건이 있을 시 $\text{IC}$가 동일하다. $\text{IC}$는 프로그램, 컴파일러의 영향을 받는다.

만약 다른 명령어의 클래스가 다른 클럭 사이클의 횟수를 취한다면,
$$\sum_{i=1}$$