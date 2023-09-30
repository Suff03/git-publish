tags: #divide-and-conquer #sort #algorithm 

- Merge Sort의 전개 과정은?
- Merge Sort의 시간 복잡도는?

---

##### 합병 정렬
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

##### Pros
어떤 `Input`이 들어오든 간에 <u>시간 복잡도가 똑같다.</u> 쪼개진 배열을 조합할 때도 $\mathcal{O}(n)$을 넘지 않는다. 즉, Merge Sort는 $\mathcal{O}(n\log n)$을 보장한다.

##### Cons
$\mathcal{O}(n)$의 추가적인 공간이 필요하다.

##### Time Complexity
Merge Sort는 [[Divide and Conquer]] 알고리즘이다.
1. `Divide` 단계에서는 중간점을 계산한다. $\mathcal{O}(1)$ 시간이 소요된다.
2. `Conquer` 단계에서는 재귀적으로 $2/n$의 두 개의 하위 배열을 정렬한다.
3. `Merge` 단계에서는 $\mathcal{O}(n)$만큼 $n$개의 요소를 정렬한다. 

따라서,
$$ T(n)=2T(n/2)+\Theta(n)$$
이를 만족한다.

![[KakaoTalk_20230922_134500446.jpg]]
* Best : $\mathcal{O}(n\log n)$
* Worst : $\mathcal{O}(n\log n)$