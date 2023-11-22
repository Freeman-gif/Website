## credit: Mikkel, Freeman
# Model Validation & Diagnosis


---
### Modeling problems:

- Data scrtuctural problems
	- Multicollinearity
	- Influential points
- Model assumption violatings 
	- Heteroscedastiticy
	- Non-nomrality residuals
	- y and x are not linearly related but modeled that way
		- false assumption of linearity between y and predictors
- For all the modeling problems, we will break down to;
	- Damage it might cause
	- Detection
	- Solution


---

#### Multicollinearity:
- **Problem**: 
	- two or more of the predictors are highly correlated or in broader description, one of the columns of $\vec{x}^{T}\vec{x}$ is a linear combination of the others, i.e $\vec{x}^{T}\vec{x}$ is close to non-invertible
- **Damage**: 
	let model be OLSE, then $\vec{b}=\left(\vec{x}^{\top} \vec{x}\right)^{-1} \cdot \vec{x} \cdot \vec{y}$
	with Multicollinearity:
	- $\operatorname{det}\left(\vec{x} ^T\vec{x}\right) \approx 0$ small value
	- $\left(\vec{x}^{\top}\vec{x}\right)^{-1}$ has vary lane values
	- small change in $\vec{x}$ causes big changes in $\vec{\beta}$, <mark style="background: #FF5582A6;">
	 - adding or dropping </mark> predictos also causes big change in $\vec{\beta}$ -> unstabale and unreliable models
##### notes: An <mark style="background: #FF5582A6;">"unstable" </mark>model refers to a model where small changes in the data result in large changes in the estimated coefficients or predictions,An "<mark style="background: #FF5582A6;">unreliable</mark>" model is one you cannot trust to make accurate predictions or inferences.





![[Pasted image 20230925210834.png]]

**Test result unreliable**:
- Test result unreliable due to the inflation in $se(\hat{\beta_{k}})$:
	- in t-test: $t_{stat}=\frac{\hat{\beta_{k}}}{se(\hat\beta_{k})}$ - result small t stat values
	->$Se(\hat{\beta_{k}})=$ $M S E \cdot\left[\left(\left(\vec{x}^{\top} \vec{x}\right)^{-1}\right]_{k+1, k+1}\right.$
	- $\left(\vec{x}^{\top} \vec{x}\right)^{-1}$ will produce large values which end up inflat the $Se(\hat{\beta_{k}})$ -- inflated standard error (P-value)
- **Symptoms**:
1. very few significant t tests, very wide C.I.S
2. **High R-squared but Few Significant Predictors**
3. The inflation in se causes smaller t statistic, which makes it harder to have a rejection / significant predictor when having a lot of predictors in the model

- **F test**:
	- **Insignificant F-test Despite Strong Theoretical Rationale**: Sometimes, despite strong theoretical reasons or prior evidence to believe that predictors should be associated with the response, the overall F-test might not be significant. This can be due to multicollinearity diluting the apparent effect of each predictor.


	- **Symptoms**:
		- Very few coef show significance from t-test
		- in ANOVA(type=1), changing the order of variables, the significance might change dramatically
		- ex: ![[Pasted image 20230925211015.png]]
#### notes:
- In reality, <mark style="background: #FF5582A6;">it always exists</mark>. when its not too serious, we dont need to worry about it too much
- It affects more in the model interference: testing. it becomes difficult for us to examine the relationship between each predictor and response variable independently
- <mark style="background: #FF5582A6;">**DETECTION**:</mark>

-  Plot heatmap of parwise correlation between predictors
- Variance Inflation Factor (VIF), most common. VIF measures how much the variance is inflated in the coef estimates
- VIF for $\hat{\beta_{j}}$ is
- $VIF_{j}=\frac{1}{1-R^2_{j}}$, where $R^2_{j}$ is obtained by regressing $X_{j}$ against the rest p-2 predictors
	- VIF=1: we dont lose any cariation without $X_{J}$, aka its not correlated with any other predictors / the cariance in $X_{j}$ is not inflated at all
	-  VIF=1-4: light (fine)
	- VIF=4-10 moderate (fine)
	- VIF greater than 10: $CX_{j}$ is highly impacted by the multicollinearity
- **Solution**:
	- Drop some highly correlated predictors based on practical understanding
	- linearly combine some independent variables together when it makes sense: like when they are on the same scale (dimension, depth + length+ width) or define a new one
			- EX. BMI instead of height and weight
###### NOTES:
- <mark style="background: #FF5582A6;">don't drop intercept easily</mark>
- If dropping one or two variables doesnt help, you dont have to drop more. Its a balance between inflation and information (battle between overfitting and underfitting)
---
#### Influential points
- **Why**:
	- data points can potentially be influential to your model in different ways:
	- Outlier: an observation has a response <mark style="background: #FF5582A6;">value $y_{i}$</mark> that is very far from the <mark style="background: #FF5582A6;">fitted value $\hat{y}_{i}$</mark>
	- High leverage point: <mark style="background: #FF5582A6;">an observation has a particular unusual combination of predictor</mark> values is said to have high leverage, that could interfere $\hat{y}_{i}$
	- Observations thats an outlier with high leverage
- **Problem**:
	- The influential points significantly affect the model estimation: with or without the observations lead to significantly different models
 - **Damages**:
	 - Unstable model results
	 - Change the scope of the data and violate model assumptions
	
**Detection**:
Recall : True model $\vec{y}=\vec{x} \cdot \vec{\beta}+\vec{\varepsilon}$
OLSE: $\vec{b}=\left(\vec{x}^{\top} \vec{x}\right)+\vec{x}^{T} \vec{y}$
Fitted Value:$\hat{\vec{y}}=\vec{x} \vec{\beta}$
$$-> \vec{x}\left(\vec{x}^{\top} \vec{x}\right)^{-1}\vec{x}^{\top} \vec{y}$$
$$-> H\vec{y}$$

- ==Levage==:
$\left(\begin{array}{c}\hat{y}_1 \\ \hat{y}_2 \\ \vdots \\ \hat{y}_n\end{array}\right)=\left(\begin{array}{cccc}h_{11} & h_{12} & \cdots & h_{1 n} \\ \vdots & \vdots & & \vdots \\ \vdots & \vdots & & \vdots \\ h_{n 1} & h_{n 2} & \cdots & h_{n n}\end{array}\right)\left(\begin{array}{c}y_1 \\ y_2 \\ \vdots \\ y_n\end{array}\right)$

for observation i, we get $\hat{y_{i}}=h_{i 1} y_1+h_{i 2} y_2+\cdots+h_{i i} y_i+\cdots+h_{i n} y_n$, $h_{ii}$ quanitfies with influence that observed $y_{i}$ has on its prediction $\hat{y_{i}}$
$h_{ii}$ is the leverage of the $ith$ obs:
$$
h_{i i}=H_{i, i}=\left[\vec{x}\left(\vec{x}^{\top} \vec{x}\right)^{-1} \vec{x}^{\top}\right]_{i, i}
$$
1. $$
0 \leqslant h_{i i} \leqslant 1
$$
2. $$
\sum_{i=1}^n h_{i i}=p
$$
3. $$
\bar{h}=\frac{p}{n}
$$
4. $h_{ii}$ measures the distance between $\vec{x}_i=\left(1, x_{i 1}, \cdots, x_{i p-1}\right)$ and and $\overline{\bar{x}}=\left(1, \bar{x}_1, \bar{x}_2, \cdots, \bar{x}_{p-1}\right)$

![[Pasted image 20230925221933.png]]

<mark style="background: #FF5582A6;">**Semi Standnetized residuals:**</mark>
$$
e_i^*=\frac{e_i}{\sqrt{M S E}}
$$
- Standnetized: used the unbiased estimator of the true variance, in OLSE:
$$
\text { MSE } \longrightarrow \sigma^2
$$

- semi: $$\operatorname{Var}\left(e_i\right) \neq \sigma^2
$$

$$
\implies\vec{e}=\vec{y}-\vec{y}=\left(I_n-H\right)(\vec{y})
$$
<mark style="background: #FF5582A6;">$\operatorname{Var}(\vec{y})=\sigma^2 I_n$</mark>

$$
\begin{aligned}
& \operatorname{Var}(\vec{e})=\sigma^2\left(I_n-H\right) \\
& \operatorname{Var}\left(e_i\right)=\sigma^2\left(1-h_{i i}\right)
\end{aligned}
$$

- flag observations as outliers if $$
\left|e_i^*\right| \geqslant \epsilon
$$

<mark style="background: #FF5582A6;">Internal Studentized Residual </mark>

$$
\operatorname{studs}\left(e_i\right) \text {-internal }=\frac{e_i}{\sqrt{M S E\left(1-h_{i i}\right)}}
$$
$$
\sim t(n-p)
$$

- flag observations taht have:
- $$
\mid \text { studs }\left(e_i\right)_{\text {-internal }} \mid \geqslant t_{d / 2, d t=n-p}
$$

![[Pasted image 20230925222933.png]]

<mark style="background: #FF5582A6;">The externally studentized residual</mark>
$$
\text { Studs }\left(e_i\right)_{\text {-external }}=\frac{(e_{i})}{s e(e(i))}
$$
<mark style="background: #ABF7F7A6;">(Text book p396)</mark>
$$
=\frac{e_i}{\sqrt{\frac{\operatorname{sSE}\left(1-(h i i)-e_i^2\right.}{n-p-1}}}
$$
$$
\sim t(n-1-p)
$$
>[!NOTE] Index $i$ indicates the model using all data, $(i)$ indicates the model using data deleting obs $i$

 
- rule of using $studs(e_{i})$ to identify outliers with high influence: $studs(e_{i})\sim t(n-1-p)$ when $\lvert studs(e_{i}) \rvert\geq t_{\frac{a}{2},df=n-1-p}$, we can detect the ith obs as an outlier with high influence
<mark style="background: #FF5582A6;">Cooks distance</mark>
- More common way to detect influential points
- Again, refit the data without obersvation i, and its a combination of $e_{i}$ and $h_{ii}$
	- The cooks distance $D_{i}$ for ith obs:
		- $D_{i}=\frac{\sum(\hat{y_{j}}-\hat{y_{j(i)}})^{2}}{PMSE}=\frac{e_{i}^{2}}{PMSE}* \frac{h_{ii}}{(1-h_{ii})^2}$
		- $D_{i}$ measures directly how much all the fitted values changes after deleting ith observation
		- Rule: flag the obsercation when $D_{i}> \frac{4}{n}$
		  
![[Pasted image 20230925212215.png]]

---
#### Heteroscedasticity(clas_note_0926)
**Definition**:
	- error term is not constant
	- Assumptions of constance variance is violated:
**Problem**:
- Because OLSE assume that all residuals are drawn from a population that has a constant variance. when Heteroscedasticity happens, the regression model will be less dependable because the residuals should not follow any specific pattern
- IN OLSE, we use $\operatorname{MSE}\left(\vec{X^{\top}} \vec{x}\right)^{-1}$ as an unbiased estimate of $Var(\vec{\beta})$, and $\operatorname{se}(\hat{p} k)=\sqrt{\operatorname{MSE}(\vec{x}^{T}\vec{x})^{-1}}_{k+1,k+1}$. when the assumption of constant variance is violated, $\operatorname{se}(\hat{p} k)$ is not unbiased estimate of the the true standard deviation of $\operatorname{se}(\hat{p} k)$ anymore.
- affect on testing:
	- All the results involved the standard error because unreliable: t tests, prediction interval and confidence intervals1
---

**Detection**(https://towardsdatascience.com/linear-regression-with-ols-heteroskedasticity-and-autocorrelation-c12f1f65c13):
- plot 
	- Residuals vs Fitted Value plot: 
		- ![[Pasted image 20231010104821.png]]
		- ![[Pasted image 20231010104854.png]]
	- 
- Breusch - Pagan test(aka BP test)
	- setup:
		- give $e_i^2=\gamma_0+\gamma_1 x_{i, 1}+\cdots+\gamma_{p-1} x_{i, p-1}+\xi_i(E)$
		- $H_0: \gamma_1=\gamma_2=\cdots=\gamma_{p-1}-0$
		- $H_1$ : at lecest one $\gamma_k \neq 0, k=1, \cdots, p-1$
		- Test stat
			- $X_{\text {stat }}=n R^2$
			- Where $R^2$ is the R-square of model(E)
		- Rejection Rule:
			- Reject the null if $n R^2 \geqslant \chi_{\alpha,df=p}^2$
			- once rejected, assumptions violated and serious problem of Heteroscedastiticy
	- Remark:
		- BP test is only sensitive for the cases that $e_{i}^{2}$change with X linearity()
		- Generally, Lienar regression model is sensitive to outliers
		- Linear regression is general sensitive to outliers
		- check plot and test together 
----
**Solution**:

- outliers: deleting/inputing outliers can fixed the problem 
- mixing data from different populations could cause the violation of assumptions:
	- tailor the data
- Notation of Normality: transformation of data can improve both together(when violation of normality or residuals have funnel shape)
	- transformation:
		- on y:
			- natural log transformation(x has to be positive)
				- distance the smaller value(more <mark style="background: #FF5582A6;">spread out</mark>), and aggregate the larger value that are spread out will be closer after transformation
- In more complicated case:
	- when estimating $var(\vec{e})$ = matirx, we need to use a difference estimator than MSE($\vec{x}^{T}\vec{x}^{-1}$):
		- optional weighted least square estimation 
		<mark style="background: #ADCCFFA6;">Recall: OLSE: find $\vec{\beta}$ols to minimize $SS = \sum e_{i}^2$,WLSE:find $\vec{\beta}$wls to minize $SS_{WLS}=\sum w_{i}e_{i}^2$(weighted)</mark>
		[[Find weight]]
		[[Robust standard error]]
		
---- 
**Violation of Normality:**
- OLSE being "BLUE" odes not need normality assumption

- But $\vec{\beta}=(\vec{X}^{T}\vec{X}^{-1}\vec{X}\vec{Y})$ 
	- <mark style="background: #ADCCFFA6;">we can see $\vec{\beta}$ as a weighted sum of $y_{1}\dots y_{n}$, some extended version of C.:.T will give approx Normal distribution of $\vec{\beta}$ when sample size is large</mark> 
- summary of the problem: Normality assumption is presented but is described as less important than other assumptions in MLR. We only switch modeling approach when there's an extreme departure of y distribution from normality. (e.g when y is binary/categorical. we use logistic regression approach)
- **Detection**:
	- Q-Q plot
	- Hypothesis test for Normality:
		- skewness of residuals:
			- sample estimate of $E[(\frac{e_{i}}{\sigma})^3]$ A perfectly symmetric distribution has ==zero Skewness==
			- If skewness is less than -1 or greater than 1, the distribution is highly skewed.
			- If skewness is between -1 and -0.5 or between 0.5 and 1, the distribution is moderately skewed.
			- If skewness is between -0.5 and 0.5, the distribution is approximately symmetric.
	- Kurtosis: measure for cluster, or the tail:
		- shape 
	- Omnibus Test  k stat = $z_{1}g_{1}^2+z_{2}g_{2}^2$
	- Jarque-Bera Test
- **Soluton**:
	- if y is numeric/continous, but the shape is skewed:
		- Natural-log transformation on Y
	- If y is numeric/continous, but has different behaviors:
		- either drop some observations or model different groups seperately
	- <mark style="background: #FF5582A6;">box cox transformation </mark>$y_{\text {-new }}=\frac{y^\lambda-1}{\lambda}$
- when y is categorical, switch the model approach to a classification mdoel
---
**False assumption of linearity between Y and any predictor**




---
**Interaction terms in MLR:**
- 



#### TAGS