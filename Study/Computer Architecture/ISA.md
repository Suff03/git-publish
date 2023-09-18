<h5>Instruction Set Architecture</h5>
![[Pasted image 20230918155734.png]]
ISA는 `명령어 집합 구조`이다. 일종의 `CPU` 언어인 셈이다. 즉, 하드웨어와 소프트웨어가 서로 어떻게 소통할지 정해 놓은 규약이다. 중재자 역할이라고 말할 수 있다. 쉬운 [[Pipelining]]을 위해 만들어졌다.

ISA가 달라지면 `CPU`가 이해할 수 있는 명령어도 달라진다. 어셈블리어도 달라진다. 예시로 인텔 CPU에서 만든 실행 파일을 특정한 설정 없이 애플에서 실행하면 작동하지 않게 된다.

<h5>CISC</h5>
복잡하고 다양한 수의 가변 길이 명령어 집합. 가변 길이라는 특성 때문에 명령어의 규격화가 어려워 `Pipelining`에 한계가 존재한다. 실제로 복잡한 명령어를 자주 쓰지도 않을 뿐더러 오랫동안 명령어를 여러 클럭에 걸쳐 시행하므로 비효율적인 방법이라 말할 수 있다.

대표적으로 Intel의 x86, x86-64는 `CISC`를 따른다.
<h5>RISC</h5>
`CISC`의 문제점을 보완한 고정 길이 명령어 집합. 명령어 종류를 줄이고 길이를 고정하여 단순화했다. `Pipelining`이 쉬워 보통 한 클럭 내외로 수행한다.

[[Memory]] 접근 명령어를 load, store로 제한했다는 점에서 `load-store 구조`로 불리기도 한다. 메모리 접근을 최소화하고 [[Register]]를 적극 활용한다.

다만, 프로그램을 구성하는 명령어 수가 `CISC`에 비해 많다는 단점이 있다.