# 활성화 함수/Loss Function에 관하여


<aside>
💡 출처:

- 핸즈온 머신러닝
- [https://wikidocs.net/152768](https://wikidocs.net/152768) , [https://wikidocs.net/152766](https://wikidocs.net/152766) 한땀한땀 컴퓨터 비전 백과사전
</aside>

참고) 로지스틱 함수==시그모이드 함수, 크로스 엔트로피 == 소프트맥스 함수의 층

# 언제 무엇을 사용해야 할까?


![Untitled](/Deep%20Learning%20from%20Scratch/%ED%99%9C%EC%84%B1%ED%99%94%20%ED%95%A8%EC%88%98%20Loss%20Function%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC/Untitled.png)

![Untitled](/Deep%20Learning%20from%20Scratch/%ED%99%9C%EC%84%B1%ED%99%94%20%ED%95%A8%EC%88%98%20Loss%20Function%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC/Untitled%201.png)

# **소프트맥스 함수란?**


![Untitled](/Deep%20Learning%20from%20Scratch/%ED%99%9C%EC%84%B1%ED%99%94%20%ED%95%A8%EC%88%98%20Loss%20Function%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC/Untitled%202.png)

# **다중 레이블 분류와 다중 분류의 차이**


- 다중 분류란 단일 레이블 분류를 의미하며 입력값 하나당 하나의 클래스에만 대응할 수 있다.
- 다중 레이블 분류란 하나의 입력값이 여러개의 클래스에 대응할 수 있다.

> 적어도 출력층의 활성화 함수는 **라벨(클래스, Y)값을 포함하는 범위**여야 한다.(그래야 정상적으로 학습된다)
> 

# **활성화 함수는 왜 필요할까?**


- 신경망에 비선형성을 더해줘 데이터를 설명하는 복잡한 형상의 경계면을 만들어 낼 수 있다.

# 참고) 초기화 전략


![Untitled](/Deep%20Learning%20from%20Scratch/%ED%99%9C%EC%84%B1%ED%99%94%20%ED%95%A8%EC%88%98%20Loss%20Function%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC/Untitled%203.png)