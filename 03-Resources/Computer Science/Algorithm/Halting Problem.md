tags : #algorithm

- 정지 문제의 의의는?
- 정지 문제의 증명 과정은?

---

* The set of all [[Computational Problem]]s is uncountable
* The set of all `Algorithms` is countably infinite
* not exist a 1:1 correspondence

##### 과정

Assume that there exists an algorithm that solves the `Halting Problem`.
```c
HALT(P, x)
if P(x) halts -> return true
else -> return false
```

an algorithm _A_
```c
A(x)
if HALT(x, x) == true -> run forever
else -> return true
```

The behavior of _A(A)_
여기서 모순이 발생한다.

* If _HALT(A, A)_ -> true then _A(A)_ run forever
Impossible! because _A(A)_ halts -> _HALT(A, A)_ true

* _If HALT(A, A)_ -> false then _A(A)_ halts
Impossible! because _A(A)_ run forever -> _HALT(A, A)_ false

그러므로 정지 문제를 해결하는 알고리즘이 존재한다는 가정 자체가 잘못됐다. 따라서, 알고리즘으로 모든 문제를 해결할 수는 없다.