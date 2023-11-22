# Auto Correlation


---
#### The Autocovariance Function ( ACVF ) of {${Xt}$}at lag h is:
$$
\operatorname{Cov}\left(X_{t+h}, X_t\right)=\gamma_x(h)
$$

#### The Autocorrelation Function (ACF) of {$Xt$}at lag h is:
$$
\operatorname{Cor}\left(X_{t+h}, X_t\right)=\frac{\operatorname{Cov}\left(X_{t+h}, X_t\right)}{\operatorname{Var}\left(X_t\right)}=\frac{\gamma_x(h)}{\gamma_x(0)}=\rho(h)
$$
#### white noises for ACVF and ACF:
ACVF: 0
ACF: 0

---
Example 1(MA(1)):
- Mean is $E\left(x_t\right)=\mu$
- Variance is $\operatorname{Var}\left(x_t\right)=\sigma_{u t}^2\left(1+\theta_1^2\right)$
-  Autocorrelation function (ACF) is:
$$
\rho_1=\frac{\theta_1}{1+\theta_1^2}, \text { and } \rho_h=0 \text { for } h \geq 2
$$


Suppose that an MA(1) model is $x_t=10+w_t+.7 w_{t-1} \text {, where } w_t \stackrel{i z d}{\sim} N(0,1)$, thus the coefficient $\theta_{1}=0.7$. the theoretical ACF is given by 
$$
\rho_1=\frac{0.7}{1+0.7^2}=0.4698 \text {, and } \rho_h=0 \text { for all lags } h \geq 2
$$
###### note: That the _only nonzero value in the theoretical ACF is for lag 1_. All other autocorrelations are 0. Thus a sample ACF with a significant autocorrelation only at lag 1 is an indicator of a possible MA(1) model. 
plot will be:
![[Pasted image 20231101222531.png]]
![[Pasted image 20231101222602.png]]

---
Example 2(MA(2)):
- Mean is $E\left(x_t\right)=\mu$
- Variance is $\operatorname{Var}\left(x_t\right)=\sigma_w^2\left(1+\theta_1^2+\theta_2^2\right)$
-  Autocorrelation function (ACF) is:
$$
\rho_1=\frac{\theta_1+\theta_1 \theta_2}{1+\theta_1^2+\theta_2^2}, \rho_2=\frac{\theta_2}{1+\theta_1^2+\theta_2^2} \text {, and } \rho_h=0 \text { for } h \geq 3
$$


Suppose that an MA(2) model is $x_t=10+w_t+.5 w_{t-1}+.3 w_{t-2}$, where $w_t \stackrel{i i d}{\sim} N(0,1)$., thus the coefficient $\theta_{1}=0.5, \theta_{2}=0.3$.Because this is an MA(2), the theoretical ACF will have nonzero values only at <mark style="background: #FF5582A6;">lags 1 and 2</mark>. the theoretical ACF is given by 
$$
\rho_1=\frac{0.5+0.5 \times 0.3}{1+0.5^2+0.3^2}=0.4851
$$ 
and
$$
\rho_2=\frac{0.3}{1+0.5^2+0.3^2}=0.2239
$$

A plot of the theoretical ACF follows:
![[Pasted image 20231101223324.png]]
![[Pasted image 20231101223342.png]]

###### note: The only nonzero values in the theoretical ACF are for lags 1 and 2. Autocorrelations for higher lags are 0. So, a sample ACF with significant autocorrelations at lags 1 and 2, but non-significant autocorrelations for higher lags indicates a possible MA(2) model.
---
### Convariance property :
![[Pasted image 20231102082317.png]]
![[Pasted image 20231102082342.png]]
![[Pasted image 20231102082357.png]]
![[Pasted image 20231102083124.png]]
![[Pasted image 20231102083258.png]]
![[Pasted image 20231102085921.png]]
---
#### TAGS:
#timeseries #diagnois 