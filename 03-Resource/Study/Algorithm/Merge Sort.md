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

<h5>Pros</h5>
어떤 `Input`이 들어오든 간에 시간 복잡도가 똑같다. 쪼개진 배열을 조합할 때도 $\mathcal{O}(n)$을 넘지 않는다. 즉, Merge Sort는 $\mathcal{O}(n\log n)$을 보장한다.

<h5>Cons</h5>
$\mathcal{O}(n)$의 추가적인 공간이 필요하다.

<h5>Time Complexity</h5>
* Best : $\mathcal{O}(n\log n)$
* Worst : $\mathcal{O}(n\log n)$