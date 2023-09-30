tags : #computerarchitecture #insturction 

- ISA란?
- CISC와 RISC의 차이는?
- ISA의 설계 원칙은?
- 세 가지 연산 방법은? 
---

##### Instruction Set Architecture
![[Pasted image 20230918155734.png]]
ISA는 [[Instruction]] 집합 구조이다. 일종의 `CPU` 언어인 셈이다. 즉, 하드웨어와 소프트웨어가 서로 어떻게 소통할지 정해 놓은 규약이다. 중재자 역할이라고 말할 수 있다. 쉬운 [[Pipelining]]을 위해 만들어졌다.

ISA가 달라지면 `CPU`가 이해할 수 있는 명령어도 달라진다. 어셈블리어도 달라진다. 예시로 인텔 CPU에서 만든 실행 파일을 특정한 설정 없이 애플에서 실행하면 작동하지 않게 된다.

##### CISC
Complex Instruction Set Computer. 복잡하고 다양한 수의 가변 길이 명령어 집합. 가변 길이라는 특성 때문에 명령어의 규격화가 어려워 `Pipelining`에 한계가 존재한다. 실제로 복잡한 명령어를 자주 쓰지도 않을 뿐더러 오랫동안 명령어를 여러 클럭에 걸쳐 시행하므로 비효율적인 방법이라 말할 수 있다.

대표적으로 Intel의 x86, x86-64는 `CISC`를 따른다.

##### RISC
`CISC`의 문제점을 보완한 고정 길이 명령어 집합. 명령어 종류를 줄이고 길이를 고정하여 단순화했다. `Pipelining`이 쉬워 보통 한 클럭 내외로 수행한다.

[[Memory]] 접근 명령어를 load, store로 제한했다는 점에서 `load-store 구조`로 불리기도 한다. 메모리 접근을 최소화하고 [[Register]]를 적극 활용한다.

다만, 프로그램을 구성하는 명령어 수가 `CISC`에 비해 많다는 단점이 있다.

* RISC-V
	US Buckley에서 개발 중인 무료 오픈 소스 RISC 명령어셋 아키텍쳐다.
	상업적인 ISA보다 간단하고 쉽다.

##### Instructions
ISA 디자인 원칙
- Simplicity favors regularity
- Make the common case fast
- Smaller is faster
- Good design demands good compromises

##### Arithmetic Operations
산술 연산. [[Register]] Operator를 이용한다.

*Ex)* 1 + 2 = 3
Operands : 1, 2 (input operands), 3 (output operand)

**add 연산자**는 Three Operands를 가지며, Two Sources와 One Destination을 가진다.

```assembly
# s0 = a, s1 =b, s2 =c
add s0, s1, s2 # x8 = x9 + x18
```

Simplicity favors regularity를 만족.

##### Immediate

<u>Make the common case fast</u>

상수가 들어간 연산. **addi 연산자**를 사용한다.
```C
a = b + 6;
```

```assembly
# s0 = a, s1 = b
addi s0, s1, 6
```

addi는 오직 하나의 immediate number만 허용한다.
적은 상수를 직접적으로 사용하면서 명령어를 로드하는 시간을 줄이고 속도를 높인다.

##### Memory Operands
큰 숫자를 레지스터나 Immediate 안에 저장할 수 없다.
따라서, 메모리에 저장 되어있는 큰 숫자를 로드한다.

**Load** from Memory, **Store** at Memory