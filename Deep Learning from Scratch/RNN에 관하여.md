# RNN에 관하여


말의 맥락을 이해하려면 데이터 각각이 아니라 연속적인 시퀀스 데이터를 이해해야한다.

고로 모델 자체가 시퀀스 데이터를 처리하는데 적합해야하며,

그래서 순환 신경망을 사용한다.

![Untitled](/Deep%20Learning%20from%20Scratch/RNN%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC/Untitled.png)

이전의 데이터 연산이 다음 데이터 연산에 영향을 미치는 형태이다. state가 자기 입력이 되는 형태.

![Untitled](/Deep%20Learning%20from%20Scratch/RNN%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC/Untitled%201.png)

이전의 old state와 input vector을 이용해 new state를 계산한다.

function은 동일하다.

# **Vanilla RNN**


![Untitled](/Deep%20Learning%20from%20Scratch/RNN%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC/Untitled%202.png)

![Untitled](/Deep%20Learning%20from%20Scratch/RNN%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC/Untitled%203.png)

레이어들이 많아지면 학습하는데 어려움이 있는데, 이를 극복하기 위해 **LSTM**을 주로 사용함