# Logistic Regression


---

### model setup


$$y_{i}\sim b(1,\pi_{i} )$$
$$E[y_{i}]=\pi_{i}$$
$$Var(y_{i})=\pi_{i}(1-\pi_{i})$$
$$ y_{i} = \beta_{0}+\beta_{1}x_{i}+\epsilon_{i}, {}y ({0,1})$$
Fitted Model:
- $E[y_{i}]=\beta_{0}+\beta_{1}x_{i}$->$\pi_{i}=\beta_{0}+\beta_{1}x_{i}$($\pi_{i}$= probability of the linear model
True model of logistic regression:
$$\ln \frac{\pi_i}{1-\pi_i}=\beta_0+\beta_1 x_i$$
- - π is the probability that an observation is in a specified category of the binary Y  variable, generally called the "success probability."
	- The denominator of the model is (1 + numerator), so the answer will always be less than 1
	- The numerator $\exp \left(\beta_0+\beta_1 X_1+\ldots+\beta_k X_k\right)$ must be positive, because it is a power of a positive value $(e)$. 
---
### Model Estimation:
==recall: OLSE in MLR, find $\hat{\beta_{0}},\hat{\beta_{1}}$to minimize==
=> $\sum\left(y_i-\hat{y}_i\right)^2$
- $y_{i}$ = observe $y_{i}$
- $\hat{y}_i=\beta_0+\beta_1 x_i$-> estimate $\hat{\pi_{i}}$

- (look class notes 10.03)


---


### Problems with binary $y_{i}$

1. error $\epsilon_{i}$ is also binary not normally distributed any more:
	- $y_{i}=1,\epsilon_{i}=1-(\beta_{0}+\beta_{1}x_{i})$
	- $y_{i}=0,\epsilon_{i}=-(\beta_{0}+\beta_{1}x_{i})$
2. variance not constant ->OLS not optimal anymore
	- $Var(y_{i})=Var(\epsilon_{i})=\pi_{i}(1-\pi_{i})$(from bernuli distribution)
3. Constraints on response variable:
	- $0\leq \pi_{i}\leq 1$,$\pi_{i}=\beta_{0}+\beta_{1}x_{i}$
	- where linear function don't keep this constraint
---
### Model Estimation: 
Given :

$$
\left(\begin{array}{c}
\ln \frac{\pi_1}{1-\pi_1} \\
\vdots \\
\ln \frac{\pi n}{1-\pi n}
\end{array}\right)=\vec{x} \cdot \vec{\beta}
$$

$\hat{\vec{\beta}}_{mle}$ that maximize 
$L(\hat{\beta})=\pi f\left(y_i\right)$
where $f\left(y_i\right)=\pi_i^{y_i}\left(1-\pi_i\right)^{1-y_i}$

---
### Coefficient Interpretation

Given: 
$$
\ln \frac{\frac{1}{\pi}}{1-\frac{\hat{\pi}}{\pi}}=\hat{\beta}_0+\hat{\beta}_1 x_1+\cdots+\hat{\beta}_{p-1} x_{p-1}
$$

**Odds of success**:

$$
\frac{\operatorname{Prob} \text { (Success) }}{\operatorname{Prob} \text { (Fail) }}=\frac{\pi}{1-\pi}
$$

=> 
$$
\frac{\hat{\pi}}{1-\hat{\pi}}=e^{\hat{\beta}_0+\hat{\beta} x_1+\cdots+\hat{\beta}_{p-1} x_{p-1}}
$$

1. For numerical predictor:
	- odds ratio of $X_{1}$ = $e^{\hat{\beta}_1}$
	- meeasure the changes in odds of success when $X_{1}$ increase by 1, the change is $\left(e^{\hat{\beta}_1}-1\right) \times 100 \%$.
	- e.g:
		- $\hat{\beta}_{\text {age }}=0.0097$
$$
e^{\hat{\beta_{\text {age }}}=e^{0.0097}}=\frac{\text { odds of obese age + 1 }}{\text { odds of obese age }} = \frac{1.0097*p}{p}
$$

= 1.0097
when age increases by 1, the odds of obese increases by 0.97%.
<mark style="background: #FF5582A6;">case:</mark>
<mark style="background: #FF5582A6;">if</mark> $\hat{\beta}_k=0 \Leftrightarrow e^{\hat{\beta}_k}=1 \Rightarrow$ when $X_k \uparrow 1$, odds of success doesn't change, $X_{k}$ is not related to $\pi=\operatorname{Pr}(Y=1)$

<mark style="background: #FF5582A6;">if</mark> $\hat{\beta}_k>0 \Leftrightarrow e^{\hat{\beta}_k}>1 \Rightarrow$ when $X_k \uparrow 1$, odds of success increase by $\left(e^{\hat{\beta } k}-1\right) \times 100 \%$

<mark style="background: #FF5582A6;">if</mark> $\hat{\beta}_k<0 \Leftrightarrow e^{\hat{\beta}_k}<1 \Rightarrow$ when $X_k \uparrow 1$, odds of success increase by $\left(1-e^{\hat{\beta } k}\right) \times 100 \%$

- see (<mark style="background: #FFB86CA6;">class notes 10.05</mark>)
2. For categorical Predictors:
Given:
$$
X=\left\{\begin{array}{l}
D_1 \\
D_2 \\
D_3 \\
D_4
\end{array} \stackrel{\text { Dummy Enoding }}{\longrightarrow} D_1 D_2 D_3\right.
$$
$D_{4}$ is the reference 

$$
\frac{\hat{\pi}}{1-\hat{\pi}}=e^{\hat{\beta}_0+\hat{\beta}_1 D_1+\hat{\beta}_2 D_2+\hat{\beta}_3 D_3+\cdots}
$$
- when obs $\in D_{1}, D_{1}=1,D_{2}=0,D_{3}=0$
- odds of success ($D_{1}$) = $e^{\hat{\hat{\beta}}_0+\hat{\beta}_1+\cdots}$
- odds of success reference = when we choose $D_{4}$, which other = 0, and all other predictors the same
$$
\implies e^{\hat{\beta}_0+\hat{\beta}_1 * 0+\cdots}
$$

$e^{\hat{\beta_{1}}}$= odds of success (D1)/odds of success reference, after complie the reference level, the odds of success in $D_{1}$ is $\left(e^{\hat{\beta}_1}-1\right) * 100 \%$ different

example: (see class notes 10.05 page 10)

3. Tests in logistic Regression:
   - Wald test for individual coefficient $B_{k}$
	   - basically a t test in MLR
	- Deviane mel liklihood ratio test
		- alternative method for F test in MLR
---
**Wald test for individual coefficient $B_{k}$:**
$H_0: \beta_k=0$ V.S. $H_1: \beta_k \neq 0$
$\hat{\beta}_k \stackrel{\text { Appr }}{\sim} N\left(\beta_k, \operatorname{Var}\left(\hat{\beta}_K\right)\right)$

Test stats: $Z_{\text {stat }}^*=\frac{\hat{\beta}_{K }}{\operatorname{se}\left(\hat{\beta}_K\right)}$

rejection rule:$\mid Z^*$ stat $\mid \geqslant Z_{\alpha / 2}$
<mark style="background: #FF5582A6;">if $H_{0}$ is rejected, $X_{k}$ is a significant predictor of $\pi$</mark>

---
**Deviance likelihood Ratio Test**:
$$
H_0: Y \sim X_1+X_2 \text { Reclueed Nodel }
$$
$$
H_1: Y \sim X_1+X_2+X_3 \text { Full Model }
$$

F test compute the reduction in SSE
($S S E_{H_0}-S S E_{-H_1}$) to check the significant improvnment in $H_{1}$ model.

rejection rule: $\Delta G^2 \geqslant X^2, d f=P_{H_1}-P_{H_0}$ if rejected, $H_{1}$ is significantly better than $H_{1}$ model

![[Pasted image 20231010222725.png]]
df =1

---
### Model Diagnosis

- Multicolinearity 
	- stay the same for logistic regression(same as MLR)
- Influential points
- Not going to work:
	- MOdel Assumptions:
		- Heteroscedasticity
		- Nomality


---
Influential Points Detection
1. Pearson Residuals 2:
$$
\frac{Y_i-\hat{\pi}_i}{\sqrt{\hat{\pi}_i\left(1-\hat{\pi}_i\right)}}
$$ 

rule: $$
\left|e_i\right| \geqslant 3$$


2. Deviance Residual

$$
G^2=-2 \ln L
$$

$$
=-2 \sum_{i=1}^n\left[y_i-\ln \left(\frac{\hat{\pi}_i}{1-\frac{n_i}{\pi_i}}\right)+\ln \left(1-\frac{\hat{\pi}_i}{\pi_i}\right)\right]
$$


if $y_{i}=1$:
$$
\sqrt{-2\left(y_i\left(\ln \left(\frac{\pi_i}{1-\hat{\pi}_i}\right)+\ln \left(1-\hat{\pi}_i\right)\right)\right.}
$$
if $y_{i}=0$:


$$
-\sqrt{-2\left(y_i\left(n \frac{\hat{\pi}_i}{1-\hat{\pi}_i}+\ln \left(1-\hat{\pi}_i\right)\right)\right.}
$$

Rule :  $$
\left|e_i\right| \geqslant 3$$
---

Confusion matrix:

![[Pasted image 20231010224303.png]]
$$
\text { Precision }=\frac{T P}{T P+F P}
$$
$$
\text { Recall }=\frac{T P}{T P+F N}
$$

---
more Souce : https://online.stat.psu.edu/stat462/node/207/

#### TAGS