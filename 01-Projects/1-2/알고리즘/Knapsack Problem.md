tags : #algorithm 
- Knapsack Problem을 설명하라.
- 0-1 Knapsack Problem의 해답, 방법론 증명
- Fractional Knapsack Problem의 해답

---
##### Greedy Algorithm vs Dynamic Programming

##### Knapsack Problem
배낭의 최대 용량은 $W$이고, 집합 $S$의 물건들을 $i$라고 하자.
$i$의 무게는 $w_i$, 가치는 $b_i$이다.

가방 안에 넣을 수 있는 **최대 가치의 물건**의 집합은?

- 0-1 Knapsack Problem
	위의 배낭 문제를 좀 더 형식적으로 만든 문제. 넣으면 1, 안 넣으면 0.

- Fractional Knapsack Problem
	물건을 쪼개서 넣을 수 있음

**Ex)** 물건의 총 무게는 `50 pounds`를 넘겨선 안 된다. $W=50$

| item | $     | Pounds |
|:----:| ----- | ------ |
| $1$  | $60$  | $10$   |
| $2$  | $100$ | $20$   |
| $3$  | $120$ | $30$   |

##### 0-1 Knapsack Problem
item 2, item 3을 구매하는 방법이 있다. (최적의 해)
가치 : $220$$, $50\leq W$

다른 방법으로는,
item 1, item 2
가치 : $160$$, $30\leq W$

item1, item 3
가치 : $180$$, $40\leq W$

이 문제를 [[Dynamic Programming]]으로 풀 수 있다는 증명이 필요하다.
즉, `Optimal Substructure Property`를 가정하면 된다.

$A$를 $n$개의 item 중 최적을 이루는 부분집합이다. $A\leq W$
$A'$는 $A$에서 item $j$를 포함하지 않는 집합이다. $A'\leq W-w_j$

즉, $n-1$개의 item 중 최적을 이루는 부분집합과 같다.

만약 $A$는 $n$개의 item에서 최적이 맞지만, $A'$가 $n-1$개의 item에서 최적의 해가 아니라면 **모순**이다. $A'$보다 더 좋은 해가 존재한다는 것은 $A$보다 더 좋은 해가 존재한다는 뜻이다. 하지만 $A$를 최적을 이루는 부분집합이라고 가정했으므로 모순이다.

##### Fractional Knapsack Problem
[[Greedy Algorithm]]으로 쉽게 해결이 가능하다.

먼저 **기준**을 세운다. $\text{value}/\text{weight}$을 기준으로 세우면 item 1, item 2, item 3의 순서가 나온다. 이 순서대로 배낭을 채우기만 하면 된다.

item 1 : $10$ pounds, $60$$
item 2 : $20$ pounds, $100$$
item 3 : $30\times\frac{2}{3}$pounds, $120\times\frac{2}{3}$$

총 $240$$, $50\leq W$
