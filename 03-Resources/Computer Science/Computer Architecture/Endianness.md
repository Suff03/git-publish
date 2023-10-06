tags : #computerarchitecture 
- Endianness란?
- 빅 엔디언과 리틀 엔디언 방식의 차이

---

##### Endianness
[[Register]]와 [[Memory]] 사이의 **통신 방식**을 정해준다.

`Big-Endian`, `Little-Endian`방식이 있다.

##### Little Endian
**낮은 주소**에 **낮은 바이트** 순서대로 저장하는 방식이다.

Ex) `0x12345678` 저장
![리틀 엔디안 방식|500](https://blog.kakaocdn.net/dn/kChLx/btrwUk8xpSY/R7ZW8uqJTCztGHp3hTOf8K/img.webp)

RISC-V Memory는 리틀 엔디언 방식을 채택한다.