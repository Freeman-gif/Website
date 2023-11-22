# Diagnose for out lier detcetion


---
### Notes and Ideas:

$$\hat{\beta} = (x^{'}x)^{-1}x^{'}y$$
$$\hat{y} = x\beta$$
$$\hat{y}  = x(x^{'}x)^{-1}x^{'}y$$
hat matrix = $x(x^{'}x)^{-1}x^{'}$
- each individual of y hat how does it related to y
$$e = y_{i} - \hat{y_{i}}$$
Itempotency matrix

$$e = y(I-H)$$

$$Var(e) = \sigma^{2}(I-H)$$

$$Var(e) = \sigma^{2}(I-H)$$
we can define what is large outlier base on the varaince of the residual becasue if the variance of y is large then the residual is also large.
- **Solution**:
	- standarized residual 
		- take the residual and divide by the standard noraml
	- 

x outliers = high leverage point(check with the hat matrix)
	
---

### Key words:

---
#### TAGS