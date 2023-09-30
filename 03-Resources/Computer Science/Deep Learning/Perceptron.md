tags : #deeplearning 

---

퍼셉트론은 프랑크 러젠블라트에 의해 고안된 초기 인공 신경망으로, **다수의 입력으로부터 하나의 결과를 내보내는** [[Algorithm]]이다.

작동 원리는 실제 뇌를 구성하는 신경 세포의 뉴런의 동작과 유사하다. 퍼셉트론은 $0$과 $1$의 두 가지 값을 가질 수 있다.

<h5>Two-Input Perceptron</h5>
![[Pasted image 20230919122712.png]]
외부의 자극이 들어오면 `Node`에서는 각 `Input`에 대해 `Weight`를 적용하여 연산한다. `Node`에서 보내온 신호의 총합이 `임계값` $\theta$을 넘을 때만 활성화된다.
$$
\begin{equation}
       y = 
        \begin{cases}
            0 & \ (w_1x_1+w_2x_2\le\theta) \\
            1 & \ (w_1x_1+w_2x_2\ge\theta)
        \end{cases}
    \end{equation}
$$

가중치 $w$는 각 신호가 결과에 주는 영향력을 조절하는 요소로 작용한다. 즉, 가중치가 클수록 해당 신호가 그만큼 더 중요함을 뜻한다.

<h5>Bias</h5>
$$
\begin{equation}
       y = 
        \begin{cases}
            0 & \ (w_1x_1+w_2x_2+b\le0) \\
            1 & \ (w_1x_1+w_2x_2+b\ge0)
        \end{cases}
    \end{equation}
$$

입력 신호에 `weight`를 곱한 값과 `bias`를 합하여, 그 값이 $0$을 넘으면 $1$을 출력하고 그렇지 않으면 $0$을 출력한다.

$w$는 입력 신호가 결과에 주는 영향력을 조절하는 매개변수고
$b$는 뉴런이 얼마나 쉽게 활성화 하느냐를 조정하는 매개변수다.

이를 이용하여 단순한 [[Logic Gate]]를 구현할 수 있다.

<h5>Multilayer Perceptron</h5>![[Pasted image 20230919124651.png]]
퍼셉트론이 간단한 XOR 문제조차 해결할 수 없다는 문제로 긴 암흑기를 맞았다.

퍼셉트론은 직선 하나로 나눈 영역만 표현할 수 있다는 한계가 존재한다. 따라서, XOR 문제를 해결할 수 있는 왼쪽과 같은 비선형 영역을 해결할 수 없다. 이를 **다층 퍼셉트론**을 이용해 해결한다.

`Input Layer`와 `Output Layer`으로 구성된 단층 퍼셉트론에 `Hidden Layer`를 추가되면 이를 **Multilayer Perceptron**이라고 부른다.

![[Pasted image 20230919125550.png]]
다층 퍼셉트론을 이용해 XOR 문제를 해결할 수 있다.
이처럼 다층 퍼셉트론으로 단층으로는 표현하지 못한 것을 층을 수없이 쌓음으로 구현할 수 있다.