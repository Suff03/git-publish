계산 복잡도 이론에서 시간 복잡도는 문제를 해결하는데 걸리는 시간과 입력의 함수 관계를 가리킨다. 효율적인 `Algorithm`을 구상하기 위해 시간 복잡도를 고려해야 한다.

<h5>Asymptotic Notation</h5>
알고리즘의 수행 시간은 입력이 크기가 충분히 클 때를 분석한다. 그 때의 성능이 중요하기 때문이다. 점근적 분석을 위해 $\lim_{n\to\infty}$를 이용한다.

* 증가율이 더 빠르다 = 알고리즘이 느리게 수행된다.
* 증가율이 더 느리다 = 알고리즘이 빠르게 수행된다.

<h5>Big-O Notation</h5>
Big-O 표기법은 최악의 시간을 고려하는 경우이다. 한마디로, `이 정도 시간까지 걸릴 수 있다.`를 이야기한다. **증가율이 같거나 더 느린 함수들의 집합이다.**
$$\mathcal{O}(g(n)) = \{f(n)\mid \exists const\ c, n_0>0, \forall n\ge n_0,0\le f(n)\le cg(n)\}$$

간단히 나타내면,
$$\mathcal{O}(g(n)) = \lim_{n \to \infty }\frac{cg(n)}{f(n)}\ge 1$$

예를 들어,
$$\mathcal{O}(n^3)=\{n^3,\frac{1}{2}n^3+5,n^2+2,2n^3,\cdots\}$$

<h5>Small-o Notation</h5>
Small-o 표기법은 `어떠한 상황에도 알고리즘은 Small-o를 넘지 않는다.`를 이야기한다. **증가율이 더 느린 함수들의 집합이다.**
$$\mathcal{o}(g(n)) = \{f(n)\mid \exists const\  n_0>0,\forall const\ c, \forall n\ge n_0,0\le f(n)< cg(n)\}$$

간단히 나타내면,
$$\mathcal{o}(g(n)) = \lim_{n \to \infty }\frac{f(n)}{cg(n)}=0$$

예를 들어,
$$\mathcal{o}(n^2)=\{n,nlog(n),\cdots\}$$

<h5>Big-Ω Notation</h5>
Big-Ω 표기법은 최선의 시간을 고려하는 경우이다. 한마디로, `최소한 이정도 시간까지 걸린다.`를 이야기한다. **증가율이 같거나 더 빠른 함수들의 집합이다.**
$$\mathcal{\Omega}(g(n)) = \{f(n)\mid \exists const\ c, n_0>0, \forall n\ge n_0,0\le cg(n)\le f(n)\}$$

간단히 나타내면,
$$\mathcal{\Omega}(g(n)) = \lim_{n \to \infty }\frac{cg(n)}{f(n)}\le 1$$

예를 들어,
$$\mathcal{\Omega}(n)=\{n^2,nlog(n),2n+1,\frac{1}{2}n,\cdots\}$$

<h5>Small-ω Notation</h5>
Small-ω 표기법은 `아무리 빨라도 Small-ω보다는 느리다.`를 이야기한다. **증가율이 더 빠른 함수들의 집합이다.**
$$\mathcal{\omega}(g(n)) = \{f(n)\mid \exists const\  n_0>0,\forall const\ c, \forall n\ge n_0,0\le cg(n)< f(n)\}$$

간단히 나타내면,
$$\mathcal{\omega}(g(n)) = \lim_{n \to \infty }\frac{f(n)}{cg(n)}=\infty$$

예를 들어,
$$\mathcal{\omega}(n)=\{n^2,10nlog(n),\cdots\}$$

<h5>Big-θ Notation</h5>
Big-θ 표기법은 `이 알고리즘은 평균적으로 이 정도의 증가율을 지닌다`를 이야기한다. **증가율이 같은 함수들의 집합이다.**
$$\mathcal{\Theta}(g(n)) = \lim_{n \to \infty }\frac{cg(n)}{f(n)}=1$$

예를 들어,
$$\mathcal{\Theta}(n^2)=\{2n^2,n^2+30,\cdots\}$$

또,
$$\mathcal{\Theta}(g(n))=\mathcal{O}(g(n))\cap\mathcal{\Omega}(g(n))$$
으로 나타낼 수 있다.