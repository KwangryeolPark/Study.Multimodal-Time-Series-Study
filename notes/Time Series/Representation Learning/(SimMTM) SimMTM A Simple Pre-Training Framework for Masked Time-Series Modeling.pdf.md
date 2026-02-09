#timeseries #representation-learning #model-agnostic 
> [!PDF|노트] [[(SimMTM) SimMTM A Simple Pre-Training Framework for Masked Time-Series Modeling.pdf#page=4&selection=2139,0,2190,3&color=노트|(SimMTM) SimMTM A Simple Pre-Training Framework for Masked Time-Series Modeling, p.4]]
> > zi = X s′∈S\{si} exp(Rsi,s′ /τ ) P s′′∈S\{si} exp(Rsi,s′′ /τ ) z′, (4)
> 
> 수식적으로 보면, 가중치를 Encoder 자체로 두는 cross-attention과 동일한듯. Query는 $x$, K와 V는 masked data. $W_{q,k,v}$는 backbone.

