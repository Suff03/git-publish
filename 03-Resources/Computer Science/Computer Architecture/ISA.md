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

addi는 Sign-Extended 12-bit immediate를 사용한다.

##### Memory Operands
레지스터와 메모리가 서로 소통하는 연산자.

큰 숫자를 레지스터나 Immediate 안에 저장할 수 없다.
따라서, 메모리에 저장 되어있는 큰 숫자를 로드한다.

종류는 크게 두 가지로 나누어 진다. **Load** from Memory, **Store** at Memory

- Load
	메모리로부터 레지스터에 Data를 읽는다.

- Store
	레지스터에 있는 Data를 메모리에 저장한다.


**Load**
```assembly
lw s3, 8(zero) // read word at address 8 into s3
```
참고로, `Immediate Number` 8(zero)는 $0 + 8 = 8$로 계산한다.
`s3`는 메모리로부터 <u>Read</u>된 값이 들어갈 Destination Register이다.

**Store**
```assembly
sw t7, 0x10(zero) // write t7 into adress 16
```
레지스터 `t7`에 있는 값을 0x10(zero) ($0 + 0\text{x}10 = 0\text{x}10$) 주소의 메모리 공간에 <u>저장</u>한다.

Ex)
```C
a[12] = h + a[8];
// h in x21
// base address of a in x22
```
[[C]]언어로 작성된 이 코드는 RISC-V assembly code로 어떤 모습일까?

```assembly
lw x9, 32(x22) // base + 32
add x9, x21, x9 // x9 <- h + a[8]
sw x9, 48(x22) // store x9 at a[12]
```

**해석**
```assembly
lw x9, 32(x22)
```

메모리 주소 32(x22) 즉, x22(Base address : a[0]의 주소) + 32(8칸) = a[8]의 값을 `Word` 단위로 `Load` 해서 x9에 저장해라.

```assembly
add x9, x21, x9
```

`add` 연산자는 `Register Operator`이다. x21(h의 주소)의 값과 x9의 값을 더한 후, x9에 저장해라.

```assembly
sw x9, 48(x22)
```
레지스터 x9에 있는 값을 48(x22) 즉, x22 + 48(12칸) = a[12]에 저장해라.

레지스터는 메모리보다 빠르다. 메모리를 동반한 연산은 `load`와 `store`가 필요하므로, 더 많은 명령어 연산을 필요로 한다. 따라서, 컴파일러는 연산량을 줄이기 위해 레지스터를 최대한 많이 활용해야 한다. **레지스터의 최적화**가 필요하다.

##### Logical Instructions
`Logical`은 논리 게이트를 말한다.

![[Pasted image 20231010193128.png]]
`XOR` 연산은 `Parity Bit`에 자주 쓰인다.
Not 연산은 `NOT a = a XOR -1`을 통해 수행한다.

`immediate`와 논리 연산을 할 시, `Sign-Extended`를 고려해야 한다.

##### Shift Instructions
`Bit`의 포지션을 변경한다.
RISC-V에서 레지스터의 크기는 32-bit이므로, `0 ~ 31`번 까지 Shift 연산이 가능하다. 따라서, 레지스터의 끝의 `5-bit`만 받을 수 있다.

- sll - `<<`
왼쪽으로 비트 연산을 수행한다. 빈 공간을 0으로 채운다.

- srl - `>>`
오른쪽으로 비트 연산을 수행한다. 빈 공간을 0으로 채운다.

- sra - `>>>`
산술 연산이다. 오른쪽으로 비트 연산을 수행한다. 빈 공간을 Sign bit로 채운다. `MSB`

##### Branch Instructions
![[Drawing 2023-10-10 19.43.12.excalidraw|600]]
다음에 실행할 명령어의 주소를 저장하는 `Program Counter` 레지스터가 `branch` 명령어를 만나면, `PC`값을 변경시킨다. 그리고 변경된 주소로 이동하여 명령을 수행한다.

`Branch Instructions`는 크게 ==두 가지==로 나누어 진다.

![[Pasted image 20231010195546.png]]

- Conditional
	조건에 따라... `A or B`

- Unconditional
	조건 X, 다른 pc로 `jump`

##### Basic Block
![[Drawing 2023-10-10 19.48.32.excalidraw|500]]
한 번 [[Instruction]]이 수행되면, **반드시 끝까지 수행**되는 공간.

`jump`를 통해 다른 곳에서 들어오거나(처음 제외), `branch`를 통해 다른 곳으로 나가는 곳이 없어야 한다.(마지막 제외)

프로세스의 성능을 측정하는 중요한 지표가 된다. branch 명령어가 많을 수록 성능이 저하되기 때문이다.

보통 size는 4에서 5 정도 된다.