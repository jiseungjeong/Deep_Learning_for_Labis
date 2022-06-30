# CNN에 관하여


<aside>
💡 출처: [https://wikidocs.net/152775](https://wikidocs.net/152775)

</aside>

**kernel==filter==mask**(이미지의 원하는 일부분만 고려함, 원하는 특징(피쳐)만 추출) → 일반적으로 정사각행렬(2,2),(3,3)

학습의 대상은 필터 파라미터임.

# CNN의 의의


> MLP에서는 학습시켜야하는 weight가 많아 많은 파라미터를 필요로 하지만, CNN에서는 모든 입력 노드에 하나의 필터를 적용하여 파라미터의 수 엄청 감소 -> **연산속도와 효율성 상승**
> 

# **풀링**


- Feature map의 Weight parameter 수를 줄이는 역할을 함.(필터를 적용하여 input 사이즈 줄이는 역할)
- Hyper parameter: filter_size(f), stride(s)
- 일반적으로 average pooling보다 max pooling의 성능이 좋다고 여겨져 max pooling을 더 자주 사용함
- Average pooling은 sharp feature을 포착하는데 어려움을 겪음
- 일반적으로 활성화 함수에서 0 이하의 값들은 잘 취급되지 않기 때문에(ReLU) Min pooling을 사용하게 되면 significant한 정보들을 잃어버릴 수 있음**> 고로 max pooling이 일반적으로 가장 많이 사용됨**