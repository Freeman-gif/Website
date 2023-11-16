# Model Selection Metrics


---
### Metrics:
- $R^2$ -> <mark style="background: #ADCCFFA6;">equivalent to SSE, RMSE. Focus on prediction performance </mark>
- adj-$R^2$ <mark style="background: #ADCCFFA6;">-> evaluate both SSE and df (n-p), in MLR, adj-$R^2$ than $R^2$</mark>
- t test p-values(or F test p-values) -> <mark style="background: #ADCCFFA6;">focus on the statistical significance of predictors</mark>
- AIC and BIC:
	- Akaike's Information criterion(AIC):
		- AIC = $2p-2\ln(\hat{L})$ (p: number of parameters, $\hat{l}$ is the sample likelihood of the model):
			- <mark style="background: #ADCCFFA6;">2p is a penalty on the number of predictors, adding more predictors might cause increase in AIC</mark>
			- AIC tends to choose model with large likelihood, without adding too many predictors
			- 
		- <mark style="background: #FF5582A6;">smaller ALC indicate better model </mark>
	- Bayesian Information criterion
		- BIC = $\ln n*p-2\ln(\hat{l})$
			- <mark style="background: #ADCCFFA6;">ln n is a much larger penalty on adding predictors to the model </mark>
	- **Select model with the smallest AIC/BIC, they most of the time agree**.<mark style="background: #FF5582A6;"> if not, BIC picks shorter models, therefore more popular in MLR</mark>
- Mallow's Cp:
	- a good cp: 
		- $C_{p} =k$
		- then choose one with smallest cp
		- 



---

### Key words:

---
#### TAGS