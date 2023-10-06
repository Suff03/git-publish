tags : #computerarchitecture 
- MSB란?
- Unsigned Number의 의미, 식과 범위
- Signed Number의 의미, 식과 범위
- 부호 유무에 따른 수를 확장하는 방법의 차이, RISC-V에서의 명령어 차이

---

##### MSB
Signed에서, **MSB**(최상위 비트)가 $0$이면 양수, $1$이면 음수를 나타낸다.

##### Unsigned Number
**Unsigned**는 '부호가 없는'을 의미한다.
$$\text{x} : X=X_{n-1}2^{n-1}+X_{n-2}2^{n-2}+\dots+X_{1}2^{1}+X_{0}2^{0}$$
따라서, $n \text{-bit} : 0 \text{ to } 2^n-1$

- Zero Extension
부호 없는 수를 확장할 때, $0$으로 남은 부분을 채운다.
![[Pasted image 20231005162030.png]]
 
##### Signed Number
부호가 있는 수. `MSB`에 따라 부호가 달라진다.
$$\text{x} : X=-X_{n-1}2^{n-1}+X_{n-2}2^{n-2}+\dots+X_{1}2^{1}+X_{0}2^{0}$$
`2's Compliment` 개념을 사용한다.

따라서, $n \text{-bit} : -2^{n-1} \text{ to } 2^{n-1}-1$

- Sign Extension
부호 있는 수를 확장할 때, `MSB`를 확장한다.
![[Pasted image 20231005161927.png]]

##### In RISC-V Instructon Set
`word`가 아닌 `byte` 단위로 데이터를 Load하면 레지스터의 크기와 맞지 않는 경우가 생긴다. 비어있는 공간을 채우기 위한 방법이 부호 존재 유무에 따라 다르다.

`lb` : signed number loaded byte
`lbu` : zero-extended loaded byte