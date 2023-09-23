최댓값 및 최솟값을 찾아내는 연산을 빠르게 하기 위해 [[Binary Tree]]기반의 Priority [[Queue]]를 기본으로 한 자료구조.

이를 활용한 정렬 방법인 [[Heap Sort]]도 존재한다.

<h5>Binary Heap</h5>
`Heap` 중에서 가장 널리 쓰이는 형태 중 하나인 이진 힙을 이용하여 구현한다. [[Binary Tree#^685525|Complete Binary Heap]]을 사용한다.

<h5>Build Heap</h5>
![[Pasted image 20230923164057.png]]
트리의 뒤에서 부터 확인 했을 때 처음으로 자식 노드를 가지는 노드부터 `heapify`를 실행한다.

즉, `heapify`를 사용할 수 있는 가장 작은 단위부터 차곡차곡 쌓아 올려간다.

<h5>Psudocode</h5>
```python
BUILD-MAX-HEAP(A, n)
	for i <- n/2 down to 1 # 처음으로 자식 노드를 가지는 노드부터.. 
		do MAX-HEAPIFY(A, i, n)
```

<h5>Time Complexity</h5>
$height\ h$에는  $\lceil \frac{n}{2^{h+1}}\rceil$의 노드까지 최대한으로 존재할 수 있다. 
$$\text{nodes of height h}\leq \lceil \frac{n}{2^{h+1}}\rceil$$
그리고, Heap의 $height\ h$는 $\lfloor \log n\rfloor$이다.
exchange는 $\mathcal{O}(1)$이다.

따라서,
![[KakaoTalk_20230923_173444623.jpg]]
$$\sum_{h=0}^{\lfloor \log n\rfloor}\lceil \frac{n}{2^{h+1}}\rceil\mathcal{O}(h)=\mathcal{O}(n\sum_{h=0}^{\lfloor \log n\rfloor}\frac{h}{2^{h}})=\mathcal{O}(n\sum_{h=0}^{\infty}\frac{h}{2^{h}})$$
를 만족한다.

$\sum_{h=0}^{\infty}\frac{h}{2^{h}}$은 테일러 정리의 변형을 이용하여 간단히 풀 수 있다.
$$\sum_{n=0}^{\infty}nx^n=\frac{x}{(1-x)^2}$$
$x$에 $1/2$을 대입하면,
$$
\sum_{h=0}^{\infty}\frac{h}{2^{h}}=\frac{1/2}{(1-1/2)^2}=2
$$

따라서,
$$\sum_{h=0}^{\lfloor \log n\rfloor}\lceil \frac{n}{2^{h+1}}\rceil\mathcal{O}(h)=\mathcal{O}(n)$$
`Build heap`의 시간 복잡도는 $\mathcal{O}(n)$이다.

