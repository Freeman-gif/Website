#### Author: Freeman Chen
#### Data: 2023-07-07
#### Class: MSDS 504
---
1.

(a). The outcome space $s$ of this experiment is the the sum of top faces that recorded which are {2,3,4,5,6,7,8,9,10,11,12}

(b). The sets that outcome will be 5 :
{(dice1 = 1, dice2 = 4),(dice1 = 4, dice2 = 1),(dice1 = 2, dice2 = 3),(dice1 = 3, dice2 = 2)}
$$P(5)= 4* \frac{1}{6*6}=\frac{1}{9}$$

(c) The sets that outcome will be divisible by 5 will be the sum that equal to 5 and 10. since we are only counting (5,5) once so the number of favorable outcome will be 7. 
P(outcome will be divisible by 5  ) = $$\frac{7}{36}$$

---
2.
From the Theorem we know that for $P(A_{i})$ is a probability measure function, it must satisfy:
	- $P(A) \ge 0$, $\forall A$ $\in S$ 
	- $P(S) =1$
	- if $A_{1},A_{2}\dots.$ are mutually exclusive
*(a)* Prove Q is a probability measure on S:
		- Since $P$ is a probability measure of sample space $S$ $A\in S$, $P(A)$ satisfy the Theorem above. Given that $Q(A) = P(A)^2$, with $P(A) \ge 0$, $\forall A$ $\in S$. $P(A)^2$ would also satisfy this condition.\. 
		- the CDF of the interval is squared, it still continuous and will still get to 1. Because there will exist a value $x$ such that $P(X=x) = 1$, and when we square that we should still get 1. 
		- Since $A_{1},A_{2}\dots.$ are mutually exclusive. Therefore, $P(A_{1}\cup A_{2})=P(A_{1})+P(A_{2})$ let $A_{1}= \frac{1}{2}$ and $A_{2} =\frac{1}{4}$.
	$\implies Q= P(A_{1}\cup A_{2})^2=P(\frac{1}{2}+\frac{1}{4})^2=\frac{9}{16}$
	or it could rewrite as $P(A_{1})^2+P(A_{2}^2)=\frac{1}{2}^2+\frac{1}{4}^2=\frac{5}{16}$ Contradiction.Therefore, Q is ==not a probability measure== on S.
	*(b)* Prove R is a probability measure on S:
		- Scine $P(A)\ge 0$,Then $\frac{P(A)}{2} \ge 0$, thus $R(A)\ge 0$
		- Since $A\in S$ and $A$ is a probability measure, so there exist a value $A$ such that $P(A=a)=1$, $R(A) = \frac{P(A=a)}{2}=\frac{1}{2}$, thus R is ==not a probability measure for S==
	
	

	
	

---
3.
(a). $P(A\cup B)=P(A)+P(B)-P(A\cap B)$
$=0.4+0.5-0.3=0.6$
(b).$P(A\cap B')= P(A \cup B)- P(B)$
$=0.6-0.5 = 0.1$
(c).$P(A'\cap B')=(A\cup B)' = 1-0.3 =0.7$

---
4.
From the theorem5, gives that $P(A\cup B) = P(A) + P(B)-P(A\cap B)$
Prove: 
$$P(A\cup B\cup C) = P(A)+P(B)+P(C)-P(A\cap B)-P(A\cap C)-P(B\cap C)+P(A\cap B\cap C)$$
Give $P(A\cup B\cup C)$
==(Apply theorem5)==
$\implies P((A\cup B)\cup C)$
$\implies P(A)+P(B)-P(A\cap B)+P(C)-P((A\cup B)\cap C)$
$\implies P(A)+P(B)-P(A\cap B)+P(C)-P((A\cap C)\cup(B\cap C))$==(Apply theorem5)==
$\implies P(A)+P(B)-P(A\cap B)+P(C)-(P(A\cap C)+P(B\cap C)-P(A\cap B\cap C))$
$\implies P(A)+P(B)-P(A\cap B)+P(C)-P(A\cap C)-P(B\cap C)+P(A\cap B\cap C)$

----
5.
(a) Four games {AAAA, NNNN} 2 orders
(b)Six games: base on the rule, the last game is a must win for the team who win in 6 so the combination function is $5C_{2} = \frac{5!}{2!(5!-2!)}=20$ thus, there are 20 orders to win 

---
6. The percent of the unemployed are woman:$$P(\text{unemployed women}|\text{unemployed})$$
$\implies\frac{\text{unemployed}\cap \text{woman}}{\text{Unemployed}}= \frac{0.15}{0.25}=0.6$
==60%== of the unemployed are women.

---
7. Total card in a deck: 52, 4 card is ace, the chance of second card is an - first case: 
	- first case: draw an ace from the first draw, then the second draw is also an Ace:$$\frac{\frac{4}{52}*\left( \frac{3}{51} \right)}{\frac{4}{52}}\approx .059 $$
	- second case: the first card is not ace, the second one is ace: $$\frac{\frac{48}{52}*\left( \frac{4}{51} \right)}{\frac{48}{52}}\approx .078$$

---
8. The probability of the boy choose box 1 & box 2 is $\frac{1}{2}$, the probability of box 1 for blue  with picking box1 $\frac{3}{8}* \frac{1}{2} = \frac{3}{16}$, the probability of box 2 for blue with picking box 2 $\frac{4}{6}* \frac{1}{2} =\frac{4}{12}$, and the probability for the boy to pick the blue ball is $\frac{3}{16}+\frac{4}{12} \approx 0.52$


---
9.(a) $P(A\cap B) = P(A)+P(B)-P(A\cup B)$ given that $P(A\cup B)'=0.1$ thus $P(A\cup B)=1-0.1 = 0.9$. $$\implies P(A\cap B)=0.7+0.5-0.9=0.3$$
(b)$P(A|B)= \frac{P(A\cap B)}{P(B)}=\frac{0.3}{0.5} =0 .6$  
(c)$P(B|A)=\frac{P(A\cap B)}{P(A)}=\frac{0.3}{0.7}\approx 0.429$

---
10.(a)
$$P(A_{1})=\frac{1}{4}$$
$$P(A_{2})=\frac{3}{4} * \frac{1}{3} = \frac{1}{4}$$
$$P(A_{3})=\frac{3}{4} * \frac{2}{3}* \frac{1}{2} = \frac{1}{4} $$
$$P(A_{4})=\frac{3}{4} * \frac{2}{3}* \frac{1}{2} * 1 = \frac{1}{4}$$

(b)
at least on match = $(A_{1}\cup A_{2} \cup A_{3} \cup A_{4})$==Apply # Inclusion–exclusion principle==
$$\implies P(A_{1}\cup A_{2}\cup A_{3}\cup A_{4})= P(A_{1})+P(A_{2})+P(A_{3})+P(A_{4})-$$
$$P(A_{1}\cap A_{2})-P(A_{1}\cap A_{3})-P(A_{1}\cap A_{4})-P(A_{2}\cap A_{3})-P(A_{2}\cap A_{4})-$$ $$P(A_{3}\cap A_{4})
+P(A_{1}\cap A_{2}\cap A_{3})+P(A_{1}\cap A_{2}\cap A_{4})+P(A_{1}\cap A_{3}\cap A_{4})$$
$$+P(A_{2}\cap A_{3}\cap A_{4})-P(A_{1}\cap A_{2}\cap A_{3}\cap A_{4})$$

$P(\text{2 match = 2 match 2 miss}) = \frac{1*1*2!}{4!}=\frac{2}{4!}$

$P(\text{3 match = 3 match 1 miss}) = \frac{1*1*1*1}{4!}$
$P(\text{All match})=\frac{1}{4!}$
->  $P(A_{1}\cup A_{2} \cup A_{3} \cup A_{4})$ = $\frac{1}{4} *4 - \frac{2!}{4!}*6 +\frac{1}{4!}*4 - \frac{1}{4!} =\frac{21}{24}$

(c)
$P(A_{1}\cup A_{{2}}\cup\dots\cup A_{n})$
=$1- \frac{1}{2!} + \frac{1}{3!} -\frac{1}{4!}+\dots+\frac{(-1)^{n+1}}{n!}$

---
11. 
(a) Let A and B are mutually exclusive, then $P(A\cap B)= 0$, for $A$ and $B$ be independent, $A$ and $B$ must satisfy $P(A\cap B)=P(A)P(B)$ thus, mutually exclusive events can't be independent,==unless the probability of one event is zero==
(b) Let  $A$ and $B$ be independent, then $P(A\cap B)=P(A)P(B)$. as (a), the independent events can't be mutually exclusive ==unless the probability of one event is zero==
(c) Let $A \subset b$, then $P(A\cap B)=P(A)$. If $A$ and $B$ are independent, then $P(A\cap B) = P(A)P(B)$.if P(A) = 0 or P(B) =1, then the equality hold. 