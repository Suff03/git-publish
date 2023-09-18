<h5>Instruction</h5>
명령어는 [[Data]]를 움직이고 컴퓨터를 작동시키는 정보이다. 컴퓨터 프로그램은 `명령어들의 모음`으로 정의된다.

`C`, `C++`, `Java`, `Python`과 같은 프로그래밍 언어로 만든 `Source Code`는 컴퓨터 내부에서 명령어로 변환된다.

<h5>High-Level vs Low-Level</h5>
우리가 알고 있는 대부분의 프로그래밍 언어 즉, 사람이 이해하기 쉽도록 만들어진 언어를 `high-level programming language`라고 한다.

반대로 컴퓨터가 직접 이해하고 실행할 수 있는 언어를 `low-level programming language`라고 한다. 저급 언어는 명령어로 이루어져있다. 고급 언어가 실행되려면 반드시 저급 언어인 명령어로 변환되어야 한다.

저급 언어에는 두 가지 종류가 있다. 바로 `Assembly Language`와 `Machine Code`이다. 

* Machine code
	기계어는 $0$또는 $1$로 이루어진 명령어 `bit`로 이루어진 언어이다.

* Assembly Language
	어셈블리어는 명령어를 인간이 해석하기 힘들다는 단점을 보완하기 위해 나온 언어이다. 이를 다루면 매우 높은 수준의 최적화가 가능하다. 하지만 기계어에 비해 가독성이 높을 뿐, 여전히 생산성이 떨어진다. 어셈블리어를 읽으면 컴퓨터가 프로그램을 어떤 절차로 실행하는지를 가장 근본적인 단계에서부터 이해할 수 있다.

<h5>Compile vs Interpreter</h5>
고급 언어는 어떻게 저급 언어로 변환될까? 고급 언어에는 크게 두 가지 방식이 있다.

* Compiled Language
	대표적으로 `C`가 있다.
	`Compiler`가 `Source Code`를 쭉 훑어보며 처음부터 끝까지 저급 언어로 컴파일한다. 컴파일러를 통해 저급 언어로 변환된 코드를 `Object Code`라고 한다.

* Interpreted Language
	대표적으로 `Python`이 있다.
	`Interpreter`가 `Source Code`를 한 줄씩 저급 언어로 변환한다. $N$줄에 문법 실수가 있더라도 $N-1$줄까지 실행된다.
	
![[compiler-interpreter-working.webp]]
컴파일 언어가 인터프리터 언어보다 더 빠르다.

프로그래밍 언어는 둘 중 하나의 방식으로만 무조건적으로 작동하지 않는다. 예를 들어, `Python`도 `Compile`을 수행한다. `Java`의 경우 동시에 수행한다.