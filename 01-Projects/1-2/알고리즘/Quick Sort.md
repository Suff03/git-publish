tags : #divide-and-conquer #sort #algorithm 

* Quick Sort의 전개 과정은?
* Quick Sort의 분할 과정은?
* Quick Sort의 시간 복잡도는?
* Randomized Quick Sort의 전개 과정과 시간 복잡도는?
---
##### Procedure
![[Pasted image 20230918152713.png]]

[[Divide and Conquer]](분할 정복)를 이용한다.
```python
QUICKSORT(A, p, r)
	if p < r
		then q <- PARTITION(A, p, r) # 1 element
		QUICKSORT(A, p, q − 1)
		QUICKSORT(A, q + 1, r)
		
# Initial call is QUICKSORT(A, 1, n).
```

정렬 과정은 다음과 같다. 오름차순을 기준으로 설명한다.
	1. `List`에서 한 요소를 `Pivot`으로 선택한다.
	2. `Pivot`을 기준으로 왼쪽 리스트는 모두 `Pivot`보다 작은 값으로, 마찬가지로 오른쪽 리스트는 모두 `Pivot`보다 큰 값으로 정렬한다.
	3. `Pivot`을 기준으로 작은 값은 왼쪽, 큰 값은 오른쪽으로 리스트를 `분할`한다.
	4. 분할된 두 개의 리스트에 재귀적으로 `Quick Sort`를 수행한다.
	5. 재귀 호출이 리스트의 크기가 0, 1이 되어 더 이상 분할이 불가능할 때까지 수행한다.

##### Partition
```Python
Partition(A, p, r)
	x <- A[r] # x : Pivot
	i <- p − 1
	for j <- p to r − 1
		do if A[j] <= x # Pivot보다 j번째 요소가 작거나 같다면
			then i <- i + 1 # 그렇다면, i를 1 증가 시키고
				exchange A[i] <-> A[j] # i번째와 j번째랑 교환
	exchange A[i + 1] <-> A[r] # 끝나면 i + 1번째와 pivot을 교환
	return i + 1
```

분할 과정은 다음과 같다.
	1. 맨 오른쪽 요소를 `Pivot`으로 선택한다.
	2. i = p - 1으로 결정하고 j = p부터 시작한다.
	3. j = r - 1이 될 때까지 4번을 반복한다.
	4. 만약 j번째 요소가 `Pivot`보다 작거나 같다면 i를 1 증가 시키고 i번째 요소와 j번째 요소를 뒤바꾼다. 그리고 j를 1 증가시킨다. `Pivot`보다 작지 않다면 j를 1 증가시킨다.
	5. 반복이 모두 끝나면 i + 1번째 요소와 `Pivot`을 바꾼다.
	6. i + 1을 리턴한다.

Partion은 `Linear Time`을 가진다.
$$\mathcal{O}(n)$$
##### Time Complexity
**Worst**
![[Capture.webp]]

$$
\begin{align*}
T(n)&=T(n-1)+T(0)+\Theta(n)\\
&=T(n-1)+\Theta(n)\\
&=\Theta(n^2)
\end{align*}
$$

**Best**
![[Pasted image 20230921171045.png]]
[[Merge Sort]]랑 비슷하다.
$$
\begin{align*}
T(n)&=2T(\frac{n}{2})+\Theta(n)\\
&=\Theta(n\log n)\\
\end{align*}
$$

##### Randomized Quick Sort

왜 크기순?
분할 뒤 더이상 비교 x



`Random Pivoting`을 이용해 시간 복잡도를 $\mathcal{O}(n\log n)$으로 줄일 수 있다.
[[The Hiring Problem]]과 비슷하다.

먼저 정렬하고자 하는 원소들을 크기 순으로 $z_1,z_2,...,z_n$이라고 정의한다.
그리고, $Z_{ij}=\{z_i,z_{i+1},...,z_j\}$을 정의한다.

Quick Sort를 생각해보자. 임의의 한 쌍의 원소는 **최대 한 번** 비교된다. `pivot`하고 비교되기 때문이다. 그리고 그 피벗은 `Partition` 이후에는 더 이상 비교되지 않는다.

따라서 $X$를, $$X_{ij}= I\{z_{i}\text{ is compared to }z_j\}$$
이리고 정의할 수 있다. (비교될 시 $1$, 아닐 시 $0$)

알고리즘에 의한 총 비교 횟수는,
$$X=\sum_{i=1}^{n-1}\sum_{j=i+1}^{n}X_{ij}$$

기댓값을 계산하면,
$$
\begin{aligned}
E(X)&= E(\sum_{i=1}^{n-1}\sum_{j=i+1}^{n}X_{ij}) \\
& = \sum_{i=1}^{n-1}\sum_{j=i+1}^{n}E(X_{ij}) \\
& = \sum_{i=1}^{n-1}\sum_{j=i+1}^{n}Pr\left\{z_i\text{ is compared to }z_j\right\}
\end{aligned}$$

$Pr\left\{z_i\text{ is compared to }z_j\right\}$은 $z_i$가 `Pivot`이거나 또는, $z_j$가 `Pivot`일 확률과 같다.
$$
Pr\left\{z_i\text{ is compared to }z_j\right\} = Pr\left\{z_i\text{ or }{z_{j}}\text{ is the first pivot chosen from }Z_{ij}\right\}
$$
$z_{i}$또는 $z_j$가 피벗일 확률은 각각 $\frac{1}{j-i+1}$과 같다. ($i$부터 $j$까지의 element의 개수)

따라서, 
$$
\begin{aligned}
E(X)&= \sum_{i=1}^{n-1}\sum_{j=i+1}^{n}\frac{2}{j-i+1} \\
& = 2\sum_{i=1}^{n-1}\sum_{k=1}^{n-i}\frac{1}{k+1}<2\sum_{i=1}^{n-1}\sum_{k=1}^{n}\frac{1}{k} \\
& = \sum_{i=1}^{n-1}\mathcal{O}(\log n)\\
& = \mathcal{O}(n\log n)
\end{aligned}$$
Randomized Quick Sort의 평균 시간 복잡도는 $\mathcal{O}(n\log n)$이다.