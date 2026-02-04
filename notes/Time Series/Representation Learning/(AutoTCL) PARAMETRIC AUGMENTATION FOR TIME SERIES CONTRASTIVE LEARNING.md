#timeseries #representation-learning #contrastive-learning #model-agnostic #다읽음 

> [!PDF|노트] [[(AutoTCL) PARAMETRIC AUGMENTATION FOR TIME SERIES CONTRASTIVE LEARNING.pdf#page=7&selection=201,0,204,86&color=노트|(AutoTCL) PARAMETRIC AUGMENTATION FOR TIME SERIES CONTRASTIVE LEARNING, p.7]]
> > We follow CoST (Woo et al., 2022) network architecture. A multi-layer dilated CNN module is used for the backbone and we remove the seasonal feature disentangler module
> 
> Dilated CNN을 backbone으로 사용했다고는 하지만 이에 종속되는 방법론은 아님.

> [!PDF|노트] [[(AutoTCL) PARAMETRIC AUGMENTATION FOR TIME SERIES CONTRASTIVE LEARNING.pdf#page=7&selection=39,2,75,35&color=노트|(AutoTCL) PARAMETRIC AUGMENTATION FOR TIME SERIES CONTRASTIVE LEARNING, p.7]]
> > Their mask values h(x) a and h(x) p should be similar, compared to another point n that is far away from a, whose mask value is denoted by h(x) n . Formally, we have the following triplet loss.
> 
> $h_a, h_p, h_n$은 문맥 상으로 window가 아니라 하나의 instance 내에 하나의 시점을 가리킨다(scalar).

> [!PDF|노트] [[(AutoTCL) PARAMETRIC AUGMENTATION FOR TIME SERIES CONTRASTIVE LEARNING.pdf#page=1&selection=2,0,21,8&color=노트|(AutoTCL) PARAMETRIC AUGMENTATION FOR TIME SERIES CONTRASTIVE LEARNING, p.1]]
> > PARAMETRIC AUGMENTATION FOR TIME SERIES CONTRASTIVE LEARNING
> 
> 
> ### AutoTCL 논문 요약
> 1. 기존 Augmentation의 한계 지적
> 이 논문은 시계열 데이터에 Jittering이나 Scaling 같은 고정된 증강 기법을 적용하는 기존 SElf-Supervised Learning 방식들이 시계열의 본질적인 특성을 반영하지 못한다고 지적한다.
> 정보 이론 과점에서 볼 때, 단순히 가역적인 변환만 적용하는 것은 증강된 뷰의 entropy를 원본과 동일하게 유지하므로, 모델이 학습 과정에서 얻을 수 있는 정보 이득이 제한적이다.
> 
> 2. 학습 가능한 Augmentation
> 이러한 문제를 해결하기 위해, 논문은 시계열 데이터에서 중요한 부분과 중요하지 않은 부분을 스스로 구분하는 별도의 Augmentation Network를 제안한다.
> 이 네트워크는 입력 데이터 $x$를 받아 다음 두 가지를 만들어낸다.
> - $h$: 중요한 정보를 선택하는 마스크 (Binary).
> - $g$: $h$로 선택한 정보 $x^*$에 가역적인 변형 그 중에서도 scaling을 가하는 변환 함수
> 결과적으로 원본의 불필요한 잡음 $\Delta x$는 버리고, 중요한 정보 $x^*$는 $g$를 통해 변형한 뒤 새로운 random noise $\Delta v$를 주입함으로써, 정보 손실은 최소화하면서 엔트로피가 높은 뷰를 생성한다.
> 3. Latent Space Augmentation
> 새로운 노이즈를 주입하는 구체적인 방식으로는 Raw Data가 아닌 Latent Space에서의 마스킹을 채택. 시계열 데이터에서 Raw Data의 숫자 0은 missing data가 아닌 실제 유의미한 값일 수 있기에 원본을 직접 지우는 것은 위험하며 따라서 backbone 모델의 embedding layer 직후에 dropout(p=0.5) 방식으로 augmetatnion을 한다.
> 
> ### 이 방법론의 단점
> * 상당히 많은 loss와 hyper-parameter가 등장하기에 쉽게 사용할 수 없다.





