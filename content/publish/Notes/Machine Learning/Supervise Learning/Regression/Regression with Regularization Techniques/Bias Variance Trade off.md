# Bias Variance Trade off


---
### Notes and Ideas:
Ideally, we want the outcome as low [[Bias]] and low [[variance]]: which give us a highly consistent predictions that are close to perfect on average

[[Mean Squared Error]]

Model complexity vs. error:
- we want training and test errors to be as small as possible
- with the increase of the model complexity, the error of the training error will be reduce but the cross validation error will be going up becasue it has the tendency leading to overfiting 
- ![[Tendency]]

Sources of Model Error:
- High Bias: Being Wrong
	- Tendency of predicitons to miss true values
		- Worsened by missing information, overly-simplistic assumptions
		- Miss real patterns (underfit)
- High Variance: Being unstable
	- Tendency of preductions to fluctuate
		- Characterized by sensitivity or output to small changes in input data
		- Often due to overly complex or poorly-fit models
		- high sensitvity due to a complex model
- ireeducible Error: unavoidable reandomness 
	- Prsent in even the best possible model

##### Summary of bias-variance tradeoff:
- Model adjustments that decrease bias often increase varaicne, and vice versa
- The bias-variance tradeoff is analogous to a complexity tradeoff
- want a model elaboarte enough to not underfit, but not so exceedingly elaborate that it overfits.
	- example The Higher the degree of a polynomial regression, the more complex the model(low bias, higher variance).
	- At lower degrees, we can see visual signs of bias;
		- prediction s are too rigid to capture the curve pattern in the data
	- At higher degrees, we see visual signs of variance:
		- Predictions fluctuate wildly beacuse of the model's sensitivity
	- The goal is to find the right degree, such that the model has sufficient complexity to describe the data without overfitting




### Key words:

---
#### TAGS









