# ARIMA


---
### Models Family:
#### AR, Auto Regressive Process:
- Assumes [[stationary process]], $X_{t}$ is related to the past values ($X_{t-1},\dots,X_{t-p}$)
- future is related to the past 

#### MA, Moving- Average process:
- Assumes [[stationary process]], $X_{t}$ is related to the <mark style="background: #FF5582A6;">past errors</mark>, $Z_{t-1},\dots,Z_{t-q}$
#### I: intergrated (differencing Method):

#### SARIMA: S for seasonality (differencing Method ):

#### SARIMAX: add ex. regressor to the model
#### VAR: vector time series predictors 


--- 
### Def:
- Let {$X_{t}$} be an AR(P) process if $$X_{t}=\phi X_{t-1}+\phi X_{t-2}+\dots+\phi X_{t-p}$$ 
where {$X_{t}\sim WN(0,\sigma^2)$}  
#### Stationary Condition: 
[[stationary process]]
1. Backward Shift Operator B for AR:
	- no practical meaning 
	- a variable that can apply to $X_{t}$ which could give us $X_{t-1}$
	- ex:

consider Ar(p):
$$X_{t}=\phi_{1} X_{t-1}+\phi_{2} X_{t-2}\dots+\phi_{p} X_{t-p}+Z_{t}$$
=>let $$X_{t-1}=B*X_{t}, X_{t-2}=B^2*X_{t}$$
=>gnerating funciton of AR(P)
$$(1-\phi_{1}B-\phi_{2}\beta^2-\dots -\phi_{p}B^p)$$
where $\phi^P(B)$ is the generating function, polynomial function.


1. Backward Shift Operator B for MA:

if MA apply a backshift operator B:

apply $BZ_{t}$ on for the noise part, since MA is measure related to the past errors.
rewrite :
$$X_{t} = \theta_{1}BZ_{t}+\theta_{2}B^{2Z_{t}+\dots+\theta_{q}B^{qZ_{t}}+}Z_{t}$$
=> $$X_{t}=\theta^qB*Z_{t}$$

### In summary:
###### note: The stationarity condition for an AR(p) process is that all the roots of the characteristic polynomial should lie outside the unit circle in the complex plane. A complex number $\( x = a + bi \) must satisfy \( |x| = \sqrt{a^2 + b^2} > 1 \)$for the process to be stationary.
- AR(p): $\phi^p(B)*X_{t}=Z_{t}*$
	- if $X_{t}=(\phi^P(B)^{-1})*Z_{t}$
- MA(q): $X_{t}=\theta^q(B)*Z_{t}$
	- <mark style="background: #FF5582A6;">All MA(q) are stationary </mark>
	- if we can find a 
- when $X_{t}=\theta^q(B)*Z_{t}$ = $\sum{\lambda_{i}B^i}$
<mark style="background: #ADCCFFA6;">proof:</mark>
for a funciton to have an inverse function and be able to express as $\sum{\lambda_{i}B^i}$. the roots B for $\phi^{P(B)^{-1}}= 0$ have to be outside the unit circle:
$$|B|>1$$


Stationary condition for AR(p);
$\phi^p(B)*X_{t}=Z_{t}*$, the generating function $\phi^p(B)*X_{t}$ has all its zero solutions lie outside the unit circle in a complex plane 


#### Invertible condition for MA(q)
- A given data only observe $X_{t}$ not $Z_{t}$. we need to define what method we use to track the noise 
- how do we use observable {$X_{t}$} to get unobserved {$Z_{t}$}?
- rewrite the model only use the observed value. turn MA(q) as AR, then we can<mark style="background: #FF5582A6;"> use only ($X_{t}$) data</mark> to estimate the MA(q) model 

**Invertible Condition**:
An MA(q) model can be estimate only if it satisfy the invertible condition:
- the zero solutions of the generating function $\theta^q(B)$ are<mark style="background: #FF5582A6;"> all outside the unit circle </mark>

 
---
## ARMA process
**Def**
A stationary process ARMA(P,q), it usually describe a stationary process, where the $X_{t}$ is from 2 part of the past(AR, MA), past from the <mark style="background: #FF5582A6;">error and measurement</mark>
$$X_{t} = \phi_{1}X_{t-1}=\dots+\phi_{p}X_{t-p}+\theta_{1}X_{t-1}+..+\theta_{q}(Z_{t-q})$$

# Invertibility Condition

The invertibility condition is a critical aspect for the Moving Average (MA) component of an ARMA model. It ensures that the MA model can be inverted to become an AR model.

## Definition
All the zero solutions for the generating function $\Theta^q(B)$ must lie outside the unit circle.

## ARMA Model
An ARMA model combines both autoregressive (AR) and moving average (MA) components.

### Equation
The ARMA(p, q) model can be written as:
$X_t = \phi_1X_{t-1} + \phi_2X_{t-2} + \dots + \phi_pX_{t-p} + \Theta_1\epsilon_{t-1} + \Theta_2\epsilon_{t-2} + \dots + \Theta_q\epsilon_{t-q} + \epsilon_t$

### White Noise
The error terms $\epsilon_t$ are assumed to be white noise with a mean of zero and a variance of $\sigma^2$, denoted as:
$\epsilon_t \sim WN(0, \sigma^2)$

## Conditions for ARMA Model
An ARMA(p, q) model must satisfy both:
1. The stationarity condition for the AR component.
2. The invertibility condition for the MA component.

## Characteristic Polynomials
The characteristic polynomial for AR is given by $\Phi^p(B)$ and for MA by $\Theta^q(B)$. The solutions to these polynomials (roots) determine the stationarity and invertibility of the model.

###### note: All ARMA models assume <mark style="background: #FF5582A6;">stationary condition and invertible condition</mark> are satisfy 




---
### Modeling :
#### model estimation
- css-mle (conditional sum of square max likelihood)
	- <mark style="background: #ADCCFFA6;">Algorithm kalman filter </mark>
	- think it as a linear model , we want to estimate the parameters: $\Phi_{i},\theta_{i},\sigma^2$
	- $$X_{t} = \phi_{1}X_{t-1}=\dots+\phi_{p}X_{t-p}+\theta_{1}X_{t-1}+..+\theta_{q}(Z_{t-q})+Z_{t}$$
	- use MLE to maximize 
		- $Z_{i}\sim MVN(\vec{0},\sigma^2I)$
		- $X_{i}\sim MVN(\vec{(0)},\gamma_{n+1})$
			- where $\gamma_{n+1}=(cov(X_{t},X_{t+h}))$ is a auto-covarince matrix that contain the autocovarince for $X_{1}$
			- L3P36
			- 
#### Model estimation:
ARIMA (df, order = (p,0,q))
parameters estimated:

$\hat{\phi_{1}},\hat{\phi_{2};\hat{\theta_{1}},\hat{\theta_{2}},\dots,\hat{\theta_{q}}; \hat{\sigma^{2};}c}$
Model estimtaed;

$$
(Xt-c)=\hat{\phi_{1}(X_{t-1}-c)+\dots+\hat{\phi_{p}(X_{t-p-c})}}+\hat{\theta Z_{t-1}+\dots+\hat{\theta_{q}Z_{t-q}}}
$$
#### In sampel Estimation:
given data and create estimation for the data in sample;

| Data    | Esimtaion                                                                                         | Error                     |
| ------- | ------------------------------------------------------------------------------------------------- | ------------------------- |
| $X_{0}$ | $\hat{X_{0}}=c$                                                                                   | $e_{o}=\hat{X_{1}}-c$     |
| $X_{1}$ | $\hat{x_{1}}=\hat{\phi}(X_{1}-c)+\hat{\phi_{1}}e_{0}$                                             | $e_{1}=X_{1}-\hat{X_{1}}$ |
| $X_{2}$ | $\hat{x_{2}}=\hat{\phi}(X_{1}-c)+\hat{\phi_{1}}e_{0}+\hat{\theta_{1}}e_{1}+\hat{\theta_{2}}e_{0}$ | $e_{2}=x_{2}-\hat{x_{2}}$ |
| $\dots$ |                                                                                                   |                           |
| $X_{n}$        |                                                                                                   |                           |



- the true predictions observed values -> in sample estimation works well
- the predictions errors -> in sample estimation works well
- every step has a support error 

#### out of sample forecast:

###### Notes: depends on the orders (p,q), the forecast will quickly lose the support of real values and predictor errors. 
- ARIMA models are better at short-term forecast, not long-term
- With time step going further, it would lost the support
- long- term, all the forecast converge to the mean( flat-line), because we are losing the error term to 0 with the losing support of the error 

---

### order selection for ARMA (p,q)

#### Use plots to check is the data is stationary or not
- time series plot
- ACF plot
- PACF plot 
<mark style="background: #FF5582A6;">only work for pure AR(p) or MA(q), but not for broader cases.</mark>
[[ACF and PACF plots]]
if we can't not see a cut off from both tails off, other order selection model


#### Use AIC/BIC
- normally AIC and BIC only works for the same model class, in this cases. only compare models in ARIMA family. 
choose the model with the smallest AIC/BIC value
###### note:
fit the model with AIC the data to calculate AIC/BIC. No train-test method should be combinated here. 

#### Combine Train - validation - Test split/ Cross -Validation and predictions performance metrics
- RMSE
- MAE
- MAPE

##### Only measures the predictor error, can be used universally to compare different model approaches. 


#### forecast the unknown future
#### order selection: choose p & q
---
### prediction perfomance metrocs



---

---
#### TAGS:
#timeseries #models