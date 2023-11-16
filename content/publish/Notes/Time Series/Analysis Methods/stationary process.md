# stationary process


---
### Def:
Time series {$X_{t}$} is stationary if only if:
- $E(X_{t})$ is independent of t, mean does not change over time 
	- 
- $Var(X_{t})$ is independent of t, variance does not change over time 
- $Cov(X_{t+h},X_{t})$ is independent of t for each h, the correlation for observation between the same time lag(h) does not change. <mark style="background: #FF5582A6;">note: the correlation is ok depend on h, or how long apart the observation are.</mark> 
##### Remarks: The key characteristics of the stationary time series do  not change over time, which makes it easy to model and predict:


---

### White noise:
$$
\left\{X_t\right\} \sim W N\left(0, \sigma^2\right)
$$
- $E\left(X_t\right)=0, \forall t$
- $\operatorname{Var}\left(X_t\right)=\sigma^2, \forall t$
- $\operatorname{Cov}\left(X_{t+h}, X_t\right)=0, \forall t, h$
<mark style="background: #FF5582A6;">White noise is stationary </mark>


---
### Backward Shift Operator B:


---
#### TAGS