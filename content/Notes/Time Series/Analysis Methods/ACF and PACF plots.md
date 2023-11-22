# ACF and PACF plots


---
### PACF: Comphe
The partial auto correlation ( PACF) is measuring the direct corelation between $X_{t}$ and $X_{t-h}$

#### Idea:
example: hot dog price

| $S_{t-2}$ | $S_{t-1}$ | $S_{t}$ |
| --------- | --------- | ------- |
| Jan       | Feb       | March   |
| 

price of jan will effect feb, and feb will effect march. Which means that jan have a<mark style="background: #FF5582A6;"> indirect correlation</mark> to March. If we have a food festival on Jan and also a food festival on March, so we will have a direct correlation between those 2 events.

ACF = Cov($St_{2},S_{t}$)

-> Indirect
-> direct - PACF

to estimate PACF (An AR proces)

$$\hat{\alpha}(h)=\hat{\beta_{h}}$$

If a data has close to AR behavior: we should observed significant PACF up to order = P. 

PACF for $MA(q)\sim AR(\inf)$, which mean, it would never shut off, tails - off behavior 


For stationary data, we should take a combination. 
1. 
	if ACF plot has a tails off behavior

	PACF plot has a cut_off at lag h = p
	AR(p)

**MA(q)**;
ACF plot cut off at h = q
PACF plot tail off 
**ARMA(p,q)**:
unclear 
both cut-off, or both tail-off

---

### Key words:

---
#### TAGS