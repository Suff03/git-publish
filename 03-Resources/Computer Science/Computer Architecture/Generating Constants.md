tags : #computerarchitecture 
- 32-Bit Constants를 만드는 방법은?
- `lui` 연산의 주의점

---
##### 12-bit Signed constants
Signed Constants를 생성하기 위해 `addi`를 사용한다.

addi 연산자는, **12-bit** 크기의 immediate를 사용한다. 12-bit를 넘는 immediate는 다른 방법을 이용해야 한다.

![[Pasted image 20231005164651.png]]

##### Generating 32-bit Contants
Load Upper Immediate라는 의미의 `lui`를 사용한다.
`lui`와 `addi`를 함께 사용하여 32-Bit의 상수를 생성한다.

Ex)

```C
int a = 0xFEDC8765;
```
12-Bit를 넘으므로 immediate로 사용할 수 없다.

따라서 `lui`를 이용하면,
```assembly
# s0 = a
lui s0, 0xFEDC8
addi s0, s0, 0x765
```

**해석**
```assembly
lui s0, 0xFEDC8
```
`lui`연산은 20-bit의 immediate를 받는다.

`s0` 레지스터(32-bit)에 저장할 때 앞의 20-bit를 채우고, 나머지 뒷부분의 12-bit를 0으로 채운다.

```assembly
addi s0, s0, 0x765
```
`addi`로 `s0` 레지스터에 `lui`를 통해 Load 했던 `s0`의 레지스터 값과 0x765 값을 더한다.
즉, 나머지 12-bit 부분을 채운다고 말할 수 있다.

**여기서, 문제점이 발생한다.** `addi`연산은 `Sign-Extended immediate`를 이용한다. 만약  `addi`로 12-bit를 채우는 과정에서, 의도치 않게 `lui`로 앞의 20-bit를 분리하고 남아 있던 값이 `Sign-Extended`에 의해 부호가 **음수**가 되어버린다면 값이 달라진다.

따라서 이를 해결하기 위해 음수가 되어버린다면 `lui`로 나누었던 부분에 $1$을 더한다.
![[Pasted image 20231005170117.png]]