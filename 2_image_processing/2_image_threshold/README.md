# 2 단원. 이미지 임계처리

### 목표

1. 단순 임계처리, 적응 임계처리, Otsu 임계처리를 배울 것이다

2. cv.threshold와 cv.adaptiveThreshold를 배울 것이다

### Otsu's Binarization

우리는 이중모드 이미지를 다루고 있다. 그러므로 Otsu 알고리즘은 관계식 S에 의해 주어진 weighted within-class variance를 최소화하는 임계점 t를 찾으려할 것이다.<br>
S : σw(t)^2 = q1(t) * σ1(t)^2 + q2(t) * σ2(t)^2<br>
여기서<br>
q1(t) = ∑(i = 1 -> t)P(i) & q2(t) = ∑(i=t+1 -> I)P(i)<br>
μ1(t) = ∑(i=1 -> t)(i * P(i) / q1(t)) & μ2(t) = ∑(i=t+1 -> I)(i * P(i) / q2(t))<br>
σ1(t)^2 = ∑(i=1 -> t)(((i − μ1(t))^2) * (P(i) / q1(t))) & σ2(t)^2 = ∑(i=t+1 -> I)(((i − μ2(t))^2) * (P(i) / q2(t)))<br>
이 식을 통해 두 극대점 사이에 있어 양 클래스의 변화량이 최소가 되는 t의 값을 찾는다.

이를 실제로 파이썬으로 구현한 코드가 3번 튜토리얼이다.