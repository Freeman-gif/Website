# ACF and PACF plots



---
## ACF plots

![[Pasted image 20231121210058.png]]
![[Pasted image 20231121210106.png]]
![[Pasted image 20231121210225.png]]
![[Pasted image 20231121210130.png]]


---
## Partial Autocorrelation Function (PACF)

- PACF is a component of the Autocorrelation Function (ACF).
- The Partial Autocorrelation $ 	ext{PACF} $ at lag $ h $ is given by:

  ${PACF}(h) = cov(X_t, X_{t-h} | X_{t-1}, \ldots, X_{t-h+1}$ { are fixed}) 

  This measures the direct correlation between $X_t$ and $X_{t-h}$ when the intervening lags are controlled for.

### Idea

- Consider indirect correlation through intervening periods as demonstrated in the following example:

  January $S_{t-2}$ → Food Festival
  February $S_{t-1}$
  March $S_t$ → Food Festival

  There is direct correlation between the Food Festivals of January and March.

## Estimating PACF

- To estimate ${PACF}$ at lag $h$, consider:

$$
\left.\operatorname{cov}\left(X_t, X_t-h\right)\right|_{x_{t-1}, \ldots, X_{t-h+1}} \text { are fixed }
$$

  Where $h$ is the coefficient from Multiple Regression (MR) that measures how $X_{t-h}$ and $X_t$ are related, given all the rest are fixed.


## Interpretation of PACF

$$
\text { PACF } \hat{\alpha}(h)=\hat{\beta}_h
$$

## PACF Plots

- AR(p) shows cutoff behavior after lag $p$.
- MA(q) shows tapering off or damping behavior.
- ARMA(p,q) may show a mix of these behaviors.

## Model Selection Criteria

### AIC and BIC

Choose the model with the smallest AIC/BIC value.

**Note**: Fit the model with all the data to calculate AIC/BIC. No train-test method should be combined here.

### Key words:

---
#### TAGS:
#timeseries 