tags : #deeplearning 

---

![[Pasted image 20230919145927.png]]
활성화 함수는 입력값의 총합을 출력 신호로 바꿔주는 함수다.
모델의 복잡도를 올릴 수 있어 비선형 문제를 해결하는데 중요한 역할을 한다.

이를 수식으로 표현하면,
$$a=b+w_1x_1+w_2x_2$$
$$y=h(a)$$

$h(x)$는, 

$$
\begin{equation}
       h(x) = 
        \begin{cases}
            0 & \ (a<0) \\
            1 & \ (a\ge0)
        \end{cases}
    \end{equation}
$$

##### Feature
[[Neural Network]]에서의 활성화 함수는 주로 `Non-Linear`하다. `Linear`한 함수를 사용할 시 층을 깊게 하는 의미가 없기 때문이다.

*Ex)*
$$\begin{align*} h(x)  &= cx \\ y(x)&= h(h(h(x))) \\ &=c\times c\times c\times x \\&=c^3x&(y(x)=ax) \end{align*} $$

여러가지 활성화 함수의 종류에 대해 알아보자.

##### Step Function
![[Pasted image 20230919153955.png]]
임계값을 경계로 출력이 바뀌는 활성화 함수.
[[Perceptron]]에선 활성화 함수로 `Step Function`를 이용한다.
$$
\begin{equation}
       h(x) = 
        \begin{cases}
            0 & \ (x<0) \\
            1 & \ (x\ge0)
        \end{cases}
    \end{equation}
$$

##### Sigmoid Function
![[Pasted image 20230919154612.png]][[Backpropagation]]에 따라 가중치를 학습시키는데 미분을 사용하기 때문에 활성화 함수로 계단 함수를 사용하기 어렵다. 또한 계단 함수는 미분이 불가능할 뿐만 아니라, $0$ 또는 $1$의 극단적인 값을 전달하기 때문에 데이터의 정보를 크게 손실시켰다.

`Sigmoid Function`은 S자와 유사한 완만한 시그모이드 커브 형태를 보이는 함수다. 시그모이드의 매끈함이 신경망 학습에서 중요한 역할을 한다.
$$\sigma(x)=\frac{1}{1+e^{-x}}$$

##### ReLU Function
![[Pasted image 20230919155111.png]]
`ReLU Function`은 최근에 주로 이용되는 활성화 함수이다. `Rectified Linear Unit(정류된 선형 함수`의 뜻이다.

입력이 $0$을 넘으면 그대로 출력, $0$ 이하이면 $0$을 출력하는 간단한 형태의 함수다.
$$
\begin{equation}
       h(x) = 
        \begin{cases}
            0 & \ (x\le0) \\
            x & \ (x>0)
        \end{cases}
    \end{equation}
$$

##### Softmax Function
`Softmax Function`은 간단히 말해 총합이 $1$인 형태로 바꿔주는 함수다. [[Classification]] 문제에서 자주 사용된다.

소프트맥스 함수의 출력은 `Probability`로 해석할 수 있다. 출력이 $0$에서 $1.0$ 사이의 실수이며, 출력의 총합이 1인 성질을 가지고 있기 때문이다.

신경망을 이용한 `Classification`에서는 일반적으로 가장 큰 출력을 내는 `Neuron`에 해당하는 클래스로만 인식한다. 함수를 적용해도 출력이 가장 큰 뉴런의 위치는 달라지지 않는다. ($e^x$가 단조 증가 함수이기 때문) 결과적으로 `Output Layer`에서는 생략 가능하다.
$$\sigma(a_k) = \frac{e^{a_{k}}}{\sum_{i=1}^n e^{a_{i}}} \ \ \ for\ i=1,2,\dots,n$$

*주의점!*
컴퓨터로 계산할 때 소프트맥스 함수는 Overflow 문제가 발생하는 결함이 존재한다. $e^x$가 큰 값을 만들어내기 때문이다.

따라서 소프트맥스 함수를 일반적으로
$$\begin{align*} \sigma(a_k)=\frac{e^{a_{k}}}{\sum_{i=1}^n e^{a_{i}}}&=\frac{Ce^{a_{k}}}{C\sum_{i=1}^n e^{a_{i}}}
\\ &=\frac{e^{(a_{k}+\log C)}}{\sum_{i=1}^n e^{(a_{i}+\log C)}} \\ &=\frac{e^{(a_{k}+C')}}{\sum_{i=1}^n e^{(a_{i}+C')}}\end{align*} $$
로 변환한 다음, $C'$에 입력 신호 중 **최댓값**을 사용해서 빼준다.

##### Identity Function
`Identity Function`은 입력을 그대로 출력한다. [[Regression]] 문제에서 자주 사용된다. `Regression`에서의 출력층은 현재까지 계산된 값을 그대로 출력할 필요가 있기 때문에 항등 함수를 통해 현재까지 계산된 값을 그대로 출력한다.