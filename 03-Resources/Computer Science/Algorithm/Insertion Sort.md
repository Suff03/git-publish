tags : #algorithm 

---
##### 삽입 정렬
두 번째 자료부터 시작하여 그 앞(왼쪽)의 자료들과 비교하여 삽입할 위치를 지정한 후, 자료를 뒤로 옮기고 지정한 자리에 자료를 삽입하여 정렬하는 알고리즘이다.

```Python
for j <- 2 to n
	key <- a[j]
	i <- j - 1
	while(i > 0 and a[i] > key)
		a[i + 1] <- a[i]
		i <- i - 1
	a[i + 1] <- key
```

##### Time Complexity
* Best : $n - 1$
* Worst : $1 + 2 + 3 + ... + (n - 1) = n(n-1)/2$
