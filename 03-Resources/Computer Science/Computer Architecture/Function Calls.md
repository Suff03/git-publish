tags : #computerarchitecture 

---
##### Function(Procedure) Calls
- Caller : 함수를 호출함
- Callee : 호출 당한 함수

- 함수 호출
jump and link
![](https://blog.kakaocdn.net/dn/t4236/btrPbviDtW7/HmDOYSKcWMWYgsS8jRklZ1/img.png)jal ra, ProcedureLabel
Callee 명령어의 주소로 pc를 변경한 다음(ProcedureLabel로 점프), ra(=x1)에 복귀한 뒤 실행할 다음 명령어의 주소(pc + 4)를 넣어준다.

Caller에선 함수 전달 인자로 a0~a7을 사용한다.

- 함수 리턴
jump and link register
jalr x0, 0(ra)

복귀하기 위해 사용되는 명령어이다.
다음 명령어의 주소를 x0에 저장하고 ra 레지스터 안의 주소로 점프한다.

Caller에게 결괏값을 전달하기 위해 a0을 사용한다.
![[Pasted image 20231015191020.png]]

##### 문제점
프로시저 호출이 다른 부분에 영향을 미쳐서는 안된다.
모든 레지스터는 복귀하기 전에 프로시저 호출 상태 전으로 되돌아가야 한다.
Caller가 필요한 값을 덮어 씌우는 문제도 생길 수 있다.

Ex) callee에서 a0, a1, a2가 아닌, t0, t1, s3 등을 사용하는 경우..

이를 레지스터를 **스택**에서 일시적으로 저장함으로써 해결한다.

##### Stack
스택은 높은 주소에서 낮은 주소 쪽으로 **성장**한다.
Stack Pointer : 스택의 top의 주소를 가리키는 포인터

스택을 통해 백업 & 복원을 함

![[Pasted image 20231015192401.png]]

##### Preserve Registers
만약 Caller가 t0, t1, s3을 사용하지 않는 경우, 성능 측면에서 마이너스 요소로 작용한다.
그러한 경우를 방지하기 위해서, 레지스터를 두 가지로 분류한다.

![[Pasted image 20231015192629.png]]
- Preserved Register (Callee-Saved)
	**Caller가 사용하고 있을 확률**이 높다.
	s0-s11
	Callee 측에서 추가적으로 Stack 공간을 확보해서 사용해야 한다.
	Stack을 사용하고자 한다면, sp의 아래쪽 주소의 메모리를 사용해야 한다.

- Non-Preserved Register (Caller-Saved)
	**Callee가 사용하고 있을 확률**이 높다.
	t0-t6
	Caller측에선, 이미 확보된 공간을 활용하면 된다. (sp의 위쪽 주소의 메모리)

![[Pasted image 20231015193419.png]]

##### Non-Leaf Function
다른 함수를 `Call`하는 함수.
함수를 호출하기 전, `ra`를 스택에 보관해야 한다.

![[Pasted image 20231015193951.png]]
![[Pasted image 20231015193959.png]]

##### Recursive Functions
자기 자신을 호출하는 재귀 함수. 스택을 이용한다.

![[KakaoTalk_20231015_210829803.jpg]]
![[KakaoTalk_20231015_211027202.jpg]]