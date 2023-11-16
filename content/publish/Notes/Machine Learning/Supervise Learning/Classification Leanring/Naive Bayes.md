# Naive Bayes


---
### Notes and Ideas:
- Text classification
	- naive bayes is easy because we make a very strong(and wrong) assumption.
- Ex.
	- Basic spam classifier:
		- use proportion of spam from training set as prediction 
		- <mark style="background: #FF5582A6;">P(spam|X) </mark>where X is our features from our emails -> logistic regression 
		- prior information ( training set )
- ![[Bayes Theorem]]
- $P(\text{spam}|x)= \frac{P(\text{spam},x)}{p(x)}$ = $\frac{p(x_{1},x_{2}\dots,x_{p},\text{spam})}{p(x_{1},x_{2}\dots,x_{p})}$
- x = [$x_1,x_2...,x_p$]
- 


---

### methods:
#### Bernoulli method:
- each features $X_{i}\in{0,1}$

---
#### TAGS
#classification