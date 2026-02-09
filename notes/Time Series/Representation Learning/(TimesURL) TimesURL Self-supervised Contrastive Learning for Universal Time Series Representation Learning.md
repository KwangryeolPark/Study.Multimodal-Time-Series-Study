#timeseries #representation-learning #contrastive-learning #model-agnostic
> [!PDF|] [[(TimesURL) TimesURL Self-supervised Contrastive Learning for Universal Time Series Representation Learning.pdf#page=1&selection=89,1,91,23|(TimesURL) TimesURL Self-supervised Contrastive Learning for Universal Time Series Representation Learning, p.1]]
> > lipping (Luo et al. 2023) flip 
> 
> Flipping 같은 기법은 Time Series에서 부적절한 방법임이 PPT 논문을 통해 밝혀짐.

> [!PDF|] [[(TimesURL) TimesURL Self-supervised Contrastive Learning for Universal Time Series Representation Learning.pdf#page=1&selection=0,0,1,24|(TimesURL) TimesURL Self-supervised Contrastive Learning for Universal Time Series Representation Learning, p.1]]
> > TimesURL: Self-supervised Contrastive Learning for Universal Time Series Representation Learning
> 
>### 핵심 제안 및 방법론
>이 논문은 시계열 데이터의 Contrastive Learning에서 발생하는 Easy Negative 문제와 부적절한 증간으로 인한 정보 왜곡을 해결하기 위해 TimesURL 프레임워크를 제안한다.
>* Double Universum (Easy Negative 해결): 대부분의 negative samples이 너무 쉽게 구분이 가능하다는 점을 해결하기 위해, 앵커와 네거티브 샘플을 임베딩 공간에서 혼합하여 universum이라 불리는 고품질의 하드 네거티브를 생성한다.
>* FTAug: 시계열의 고유한 시간적 특성을 해치지 않기 위해, 주파수 도메인과 시간 도메인을 결합한 증강 기법을 사용한다.
>* 맥락적 일관성: 증강된 두 뷰에서 동일한 timestamp에 해당하는 표현 벡터끼리 positive pair를 맺도록 하여, 시간적 맥락을 유지하며 학습시킨다.
>### 한계점 및 비판
>논문의 기여에도 불구하고, 프레임워크의 구조적 제약과 데이터 처리 방식에서 다음과 같은 한계가 존재한다.
>* Representation의 차원 제약 (T축 필요): 제안된 Dual Contrastive Loss 중 시간적 대조 손실을 계산하기 위해서는 단일 시계열 내에서 서로 다른 시점을 구분할 수 있어야 한다. 따라서 모델의 출력 표현에 반드시 시간 축이 보존되어야만 이 프레임워크를 온전히 사용할 수 있다. Global Pooling 등으로 시간 축이 압축되거나 하나의 token으로 변환하는 iTransformer 같ㅇ은 모델에서는 temporal loss 적용이 불가능하다.
>* 단순한 Random Masking 전략의 한계: 논문은 Random Masking 전략을 채택하고 있으나, 이는 시계열 데이터의 높은 자기상관성을 고려하지 못한 방식이다. 랜덤하게 흩뿌려진 마스킹은 주변 값을 통해 정답을 너무 쉽게 유추할 수 있게 하여 모델이 깊이 있는 문맥을 학습하는 것을 방해할 수 있다.
>* 0(zero) 값 처리의 모호성 (Masking vs. Value): 연속적인 값을 가지는 시계열 데이터 특성상, 마스킹된 자리를 0으로 채울 경우 모델은 이를 결측(Missing)이 아닌 실제 값이 0인 데이터로 오인할 위험이 상당히 크다. NLP의 `[Mask]` 토큰과 달리, 별도의 마스크 채널 없이 0으로 대체하는 방식은 데이터의 왜곡을 초래할 수 있다.