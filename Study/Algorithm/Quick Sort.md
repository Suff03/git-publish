[[Divide and Conquer]](분할 정복)를 이용한다.

```python
QUICKSORT(A, p, r)
	if p < r
		then q <- PARTITION(A, p, r)
		QUICKSORT(A, p, q − 1)
		QUICKSORT(A, q + 1, r)
		
# Initial call is QUICKSORT(A, 1, n).
```
<h5>Procedure</h5>
![[Pasted image 20230918152713.png]]
정렬 과정은 다음과 같다. 오름차순을 기준으로 설명한다.
	1. `List`에서 한 요소를 `Pivot`으로 선택한다.
	2. `Pivot`을 기준으로 작은 값은 왼쪽, 큰 값은 오른쪽으로 리스트를 `분할`한다.
	3. `Pivot`을 기준으로 왼쪽 리스트는 모두 `Pivot`보다 작은 값으로, 마찬가지로 오른쪽 리스트는 모두 `Pivot`보다 큰 값으로 정렬한다.
	4. 분할된 두 개의 리스트에 재귀적으로 `Quick Sort`를 수행한다.
	5. 재귀 호출이 리스트의 크기가 0, 1이 되어 더 이상 분할이 불가능할 때까지 수행한다.

<h5>Partition</h5>

```Python
Partition(A, p, r)
	x <- A[r]
	i <= p − 1
	for j <- p to r − 1
		do if A[j] <= x
			then i <- i + 1
				exchange A[i] <-> A[j]
	exchange A[i + 1] <-> A[r]
	return i + 1
```
