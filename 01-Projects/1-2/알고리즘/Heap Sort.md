tags: #heap #sort #algorithm 

- Heap Sort의 전개 과정은?
- Heapify란?
- Heap Sort의 시간 복잡도는?

---

![[Pasted image 20230922171401.png|600]]
힙 정렬을 수행하기 위해서는 우선, 최대/최소 [[Heap]]을 구성해야 한다.
여기서는 최대 힙을 사용한다.

##### Procedure
![[max_heap_deletion_animation.gif]]
![[Pasted image 20230923174910.png]]
1. $n$개에 대한 이진 트리를 만든 후, 최대 힙을 구성한다
2. `Root`와 가장 마지막 노드를 바꾼 후, 가장 마지막 노드를 제외하고 새 루트 노드에 대해 최대 힙을 구성한다.
3. 노드가 한 개가 남을 때까지 이를 반복한다.

##### Heapify
주어진 자료 구조에서 Heap의 성질을 만족하도록 하는 연산

```python
MAX-HEAPIFY(A, i, n)
	l <- LEFT(i)
	r <- RIGHT(i)
	if l ≤ n and A[l] > A[i]
		then largest <- l
		else largest <- i
	if r ≤ n and A[r] > A[largest]
		then largest <- r
	if largest ≠ i
		then exchange A[i] <-> A[largest]
			MAX-HEAPIFY(A, largest, n)
```

해석
* $A[i]$와 $A[\text{LEFT}(i)]$, $A[\text{RIGHT}(i)]$를 비교한다.
* 필요한 경우(부모보다 자식이 큰 경우), `swap`을 통해 Heap 구조를 유지한다.
* 마지막 leaf에 도달하면 마지막 leaf는 자동적으로 Max-Heap이 된다. 

##### Time Complexity of Heapify
Heap의 높이를 $h$라고 할 때 $\mathcal{O(h)}$이다. $h=\log n$이므로, 시간 복잡도는 $\mathcal{O}(\log n)$

##### Heap Sort
```python
HEAPSORT(A, n)
	BUILD-MAX-HEAP(A, n)
	for i <- n downto 2
		do exchange A[1] <-> A[i]
			MAX-HEAPIFY(A, 1, i − 1)
```

##### Time Complexity
Build Max Heap : $\mathcal{O}(n)$
• for 루프 : $n-1$ times
• 요소 교환 : $\mathcal{O}(1)$
• Max Heapify : $\mathcal{O}(\log n)$

최종적으로, 시간 복잡도는 $\mathcal{O}(n\log n)$을 만족한다.