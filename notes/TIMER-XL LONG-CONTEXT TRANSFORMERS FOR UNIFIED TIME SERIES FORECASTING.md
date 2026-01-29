> [!PDF|yellow] [[TIMER-XL LONG-CONTEXT TRANSFORMERS FOR UNIFIED TIME SERIES FORECASTING.pdf#page=3&selection=4,87,5,24&color=yellow|TIMER-XL LONG-CONTEXT TRANSFORMERS FOR UNIFIED TIME SERIES FORECASTING, p.3]]
> > Among them, decoder-only Transformer
> 
> Encoder only와 Decoder only의 차이는 정보를 처리하는 방식과 예측 방식에 있다.
> * Encoder 기반: #encoder
> 	* 양방향으로 데이터를 처리하는 경향 존재(즉, Attention 모듈에서 모든 토큰을 한 번에 계산).
> 	* 입력된 전체 시퀀스를 한 번에 보고, 모든 토큰이 서로를 참조한다.
> 	* 입력 윈도우를 받아 한 번에 고정된 길이의 미래를 예측.
> 	* 전체 문맥을 파악하여 특징을 추출하는 데 강점이 있다.
> * Decoder 기반: #decoder
> 	* 단방향이며 인과적으로 데이터를 처리.
> 	* 현재 시점의 토큰은 오직 과거의 토큰들만 참조할 수 있다. 즉, 인과적으로 데이터를 처리하며, Masked Attention 방식.
> 	* 다음 토큰을 하나씩 순차적으로 예측하는 Autoregressive 방식을 사용한다.
> 	* 다양한 길이의 유연한 입력과 출력을 처리할 수 있으며, 생성형 모델에 적합.
> 	#모델구조
> 

> [!PDF|의문점] [[TIMER-XL LONG-CONTEXT TRANSFORMERS FOR UNIFIED TIME SERIES FORECASTING.pdf#page=3&selection=150,0,151,1&color=의문점|TIMER-XL LONG-CONTEXT TRANSFORMERS FOR UNIFIED TIME SERIES FORECASTING, p.3]]
> > $TP$
> 
> Q: 여기서 TP는 $T\times P$를 의미하는 건가.? #의문점
> A: #답변없음
> Thinking: $i$가 sequence index가 아니라 patch index이고, $P$가 patch length라면?

> [!PDF|답변] [[TIMER-XL LONG-CONTEXT TRANSFORMERS FOR UNIFIED TIME SERIES FORECASTING.pdf#page=4&selection=96,0,159,3|TIMER-XL LONG-CONTEXT TRANSFORMERS FOR UNIFIED TIME SERIES FORECASTING, p.4]]
> > $P (X) = NY m=1 TY i=1 p(xm,i+1|x:,≤i) = NY m=1 TY i=1 p(xm,i+1|x1,≤i, . . . , xN,≤i)$. 
> 
> Q. 여기서 모든 variables을 독립적으로 처리하는 것인가 아니면 수식적으로 동시에 처리하는 것인가. 
> A. 
> > [!PDF|] [[TIMER-XL LONG-CONTEXT TRANSFORMERS FOR UNIFIED TIME SERIES FORECASTING.pdf#page=4&selection=169,78,170,52&color=답변|TIMER-XL LONG-CONTEXT TRANSFORMERS FOR UNIFIED TIME SERIES FORECASTING, p.4]]
> > while incorporating exogenous variable correlations from other sequences
> > * 모든 변수 간의 상관관계를 활용하여 토큰을 예측하는 형식 
> > * 첫 항의 조건부 항을 보면 $\mathbf{x}_{:, \le i}$ 형식으로 돼 있다. 즉, $m$번째 variate를 구하기 위해서 모든 variates($:$)가 동원되는 방식.
> 



> 