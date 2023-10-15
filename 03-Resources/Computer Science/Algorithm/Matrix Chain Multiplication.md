tags : #algorithm 
- Matrix Chain Multiplication을 설명하라.
---
##### Matrix Chain Multiplication
주어진 $n$개의 행렬을 연쇄적으로 곱할 때, 최소의 곱셈으로 수행하는 방법
$$A_1A_2{\cdots}A_n$$
괄호를 어떻게 묶느냐에 따라(parenthesize) 연산량이 달라진다. 즉, **최적의 묶음**을 찾는다.
최적의 해는 최종적으로 두 괄호 묶음으로 이루어졌다. 각각의 괄호는 최적의 묶음으로 이루어졌다. 따라서 [[Dynamic Programming]]으로 해결이 가능하다.

##### Solution
$M[i][j]$는 $A[i]$부터 $A[j]$까지의 최적의 연산 횟수를 의미한다.
$i\leq k\leq j-1$에서,
$$M[i][j]=\min(M[i][k]+M[k+1][j]+d_{i-1}d_kd_j)$$
$i==j$일 때,
$$M[i][j]=0$$
최종적으로 구하는 것은 $M[1][n]$이다.

**Ex)**
`bottom-up` 방식으로 해결한다.
$$A_1:2\times3, A_2:3\times4, A_3:4\times3, A_4:3\times5$$

![[Drawing 2023-10-06 18.53.05.excalidraw|600]]

$M[1][1]=M[2][2]=M[3][3]=M[4][4]=0$

$M[1][2]=M[1][1]+M[2][2]+2\times3\times4=24$
$M[2][3]=M[2][2]+M[3][3]+3\times4\times3=36$
$M[3][4]=M[3][3]+M[4][4]+4\times3\times5=60$
$M[1][3]=\min(M[1][1]+M[2][3]+2\times3\times3=54, M[1][2]+M[3][3]+2\times4\times3=48)=48$
(앞의 $2\times3\times3$은 $M[1][1]$이 $2\times3$의 행렬, $M[2][3]$을 $3\times4, 4\times3\rightarrow3\times3$의 행렬의 곱으로 봄. 따라서 $2\times3,3\times3\rightarrow2\times3\times3$. 나머지도 그러하다.)

이를 계속하여 수행하면 최종적으로 $M[1][5]$를 알 수 있다.