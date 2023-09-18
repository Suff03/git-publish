<h5>합병 정렬</h5>
존 폰 노이만이 제안한 방법. [[Divide and Conquer]](분할 정복)를 이용한다.

```Python
MERGE-SORT(A, p, r)
	if p < r
		then q <- [(p + r) / 2]       # Divide
			MERGE-SORT(A, p, q)       # Conquer
			MERGE-SORT(A, q + 1, r)   # Conquer
			MERGE(A, p, q, r)         # Combine
```

![[Pasted image 20230917135309.png]]


![[Pasted image 20230917135459.png]]

<h5>Time Complexity</h5>
* Best : $nlog(n)$
* Worst : $nlog(n)$