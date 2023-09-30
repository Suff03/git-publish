tags : #computerarchitecture 
- 응답 시간(Responce Time)이란?
- 처리량(Throughput)이란?
- Elapsed Time과 CPU Time의 차이점은?
- CPU Time을 표현하는 주요 식 3개
- 평균 CPI 구하기
- MIPS의 의미와 계산식
- MIPS 측정법의 두 가지 단점

---

##### Responce Time
응답 시간. 일을 수행하는 데 얼마나 걸리는가?

##### Throughput
단위 시간 당 총 작업량. 컴퓨터 시스템의 처리 능력을 나타내는 처리량이라고 부른다.

##### Define Performance
`CPU`의 성능은 실행 시간이 적을 수록 늘어난다. 실행 시간을 기준으로 한 성능은 다음과 같다.
$$\text{Performence} = \frac{1}{\text{Excution Time}}$$

따라서, 컴퓨터 $X$와 컴퓨터 $Y$의 성능 비율은 다음과 같이 나타낼 수 있다.
$X$는 $Y$보다 $n$배 더 빠르다.
$$\frac{\text{Performence}_X}{\text{Performence}_Y} = \frac{\text{Excution Time}_Y}{\text{Excution Time}_X}=n$$

##### CPU Time
전반적인 시스템의 시간 측정에는 `Elapsed Time(경과 시간)`이 쓰인다. 이는 Processing(처리), I/O(입출력), OS overhead(운영체제 처리), Idle time(대기 시간) 등의 모든 요인을 고려한 총 `Responce Time`이라고 말할 수 있다.

`CPU Time`은 주어진 일을 처리하는 데 걸리는 시간이다. 순수한 CPU의 성능에 주목한다. 그러므로 위의 수많은 요소들을 배제한다.

그럼 CPU Time은 어떻게 구할까? 우선 [[Clock]] 개념이 필요하다.

##### Clock Cycle
CPU가 명령어를 실행하기 위해 데이터를 가져오고, 해석하고, 실행하는 단계이다.
명령어를 실행하는 주기라고 해서 명령 주기라고 부른다.

한 클럭에 걸리는 시간을 `Clock Period`, `Clock Cycle Time`이라 한다.

##### Clock Rate
CPU의 초당 클럭 사이클 수를 칭한다. `Clock Frequency`라고도 한다.

내용을 종합하면, CPU Time을 다음과 같이 표현할 수 있다.
$$\begin{align*} \text{CPU Time}&= \text{CPU Clock Cycles}\times \text{Clock Cycle Time} \\ &= \frac{\text{CPU Clock Cycles}}{\text{Clock Rate}}\end{align*}$$

성능 향상을 위해선 다음과 같은 일을 수행해야 한다.
* Reducing number of `Clock Cycles`
* Incresing `Clock Rate(Clock Frequency)

하드웨어 디자이너는 `Clock Rate`와 `Cycle Count`의 균형을 맞추어야 할 필요가 있을 것이다.

##### CPI
`CPI(명령어당 클럭 사이클 수)`는 프로그램의 특정 명령어를 수행하는데 소요되는 평균 클럭 사이클 수이다. CPU에 의해 결정되며 명령어에 따라 CPI가 다르다.

`Clock Cycles(클럭 사이클 수)`는 명령어의 개수와 명령어당 클럭 사이클 수를 곱하여 계산한다.
$$\text{Clock Cycles}=\text{Instruction Count}\times\text{Cycles per Instruction}$$

따라서 CPU Time은, 
$$\begin{align*} \text{CPU Time}&= \text{Instruction Count}\times \text{CPI}\times \text{Clock Cycle Time} \\ &= \frac{\text{CPU Clock Cycles}}{\text{Clock Rate}}\end{align*}$$

을 만족한다. 간단히 $\text{CPU Time} =\text{IC}\times \text{CPI}\times \text{C}_t$로 표현한다.

[[ISA]]가 같다는 조건이 있을 시 $\text{IC}$가 동일하다. $\text{IC}$는 프로그램, 컴파일러의 영향을 받는다.

만약 다른 명령어의 클래스가 다른 클럭 사이클의 횟수를 취한다면,
$$\text{Clock Cycles}=\sum_{i=1}^n(\text{CPI}_{i}\times\text{Instruction Count}_i)$$

평균 CPI는,
$$\text{CPI}=\frac{\text{Clock Cycles}}{\text{Instruction Count}}=\sum_{i=1}^n(\text{CPI}_{i}\times\frac{\text{Instruction Count}_i}{\text{Instruction Count}})$$

##### Performance Summary
$$
\text{CPU Time}=\frac{\text{Instructions}}{\text{Program}}\times\frac{\text{Clock Cycles}}{\text{Instruction}}\times\frac{\text{Seconds}}{\text{Clock Cycle}}$$

##### MIPS
MIPS : Millions of Instruction Per Second
컴퓨터 분야에서 연산 속도를 나타내는 약속이다. **초 당 백만 연산**의 약어.
CPU가 1초 동안 처리할 수 있는 명령어의 수. ($1\text{MIPS}$는 1초 동안 100만 개의 명령 처리)

**계산식)**
$$\text{CPU Time}=\text{IC}\times \text{CPI}\times \text{C}_t=\frac{\text{IC}\times \text{CPI}}{\text{Clock Rate}}$$
프로그램을 실행하는 데 필요한 프로세서에 대한 시간은
명령어의 개수 X CPI X Clock 주기$(1/\text{frequency})$이다.

단위 시간 당 처리할 수 있는 명령어 `IPS`는 다음과 같은 계산식을 가진다.
$$\text{IPS}=\frac{\text{IC}}{\text{T}}$$

`MIPS`는 CPU가 1초 동안 처리할 수 있는 명령어의 수를 나타낸다. $1\text{MIPS}$ 1초 동안 100만 개를 처리한다는 의미이다.
$$\text{MIPS}=\frac{\text{IC}}{\text{T}\times 10^{6}}=\frac{\text{Clock Rate}}{\text{CPI}\times10^6}$$

MIPS를 사용하기에는 **두 가지 문제점**이 존재한다.
1. MIPS는 단순히 명령어를 실행하는 속도를 나타낼 뿐이지, 그 명령어 하나가 얼마나 많은 일을 수행하는지 고려하지 않는다.
	ISA가 다른 컴퓨터는 서로 비교할 수 없다.

2. 동일한 컴퓨터 내에서도 다른 프로그램을 사용 시 CPI가 달라지므로 MIPS가 달라질 수 있다.

##### Summary
- **응답 시간**은 "일을 수행하는 데 얼마나 걸리는가?"를 의미한다.
- **처리량**은 단위 시간당 총 작업량을 의미한다. 컴퓨터 시스템의 처리 능력을 나타낸다.
- Elapsed Time과 달리 **CPU Time**은 순수한 CPU의 성능에 주목한다.
- **CPU Time**을 표현하는 주요 식 3개는,
$$\text{CPU Time}= \text{Clock Cycles}\times \text{Clock Cycle Time}$$
$$\text{CPU Time} =\text{IC}\times \text{CPI}\times \text{C}_t$$
$$
\text{CPU Time}=\frac{\text{Instructions}}{\text{Program}}\times\frac{\text{Clock Cycles}}{\text{Instruction}}\times\frac{\text{Seconds}}{\text{Clock Cycle}}$$
- **평균 CPI**
$$\text{CPI}=\frac{\text{Clock Cycles}}{\text{Instruction Count}}=\sum_{i=1}^n(\text{CPI}_{i}\times\frac{\text{Instruction Count}_i}{\text{Instruction Count}})$$
- **MIPS**는 연산 속도를 나타낸다. CPU가 1초 동안 처리할 수 있는 명령어 수를 나타낸다.
$$\text{MIPS}=\frac{\text{IC}}{\text{T}\times 10^{6}}=\frac{\text{Clock Rate}}{\text{CPI}\times10^6}$$
- **MIPS**는 명령어 하나가 얼마나 많은 일을 수행하는지 고려하지 않는다. 또, 동일한 컴퓨터 내에서도 다른 프로그램을 사용 시 CPI가 달라지므로 MIPS가 달라진다.