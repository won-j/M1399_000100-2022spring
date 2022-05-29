---
 title: "Homework 4"
 author: "M1399.000100, Seoul National University, Spring 2022"
 date: "Due 23:59 Sunday, 2022-06-19"
 output: html_document
---

# M1399.0001000 Homework 4, Spring 2021, Seoul National University
Due 23:59 2022-06-19

#### **No late submission is accepted**. 


## Q1. Textbook problems

1. 심송용 연습문제 8.2, 8.3, 8.4.

<!--
## Q2. Acceptance-rejection sampling

Suppose we want to generate samples from a Beta($\alpha$,$\beta$) distribution, whose density is given by
$$
f(x) = \frac{x^{\alpha-1}(1-x)^{\beta-1}}{B(\alpha,\beta)}~~(0<x<1), \quad B(\alpha,\beta) = \int_0^1 x^{\alpha-1}(1-x)^{\beta-1}dx.
$$

1. Write an acceptance-rejection sampling algorithm for generating a Beta random variable, in which two independent uniform random variables are generated and the density function is explicitly used. 

2. Find the probability of acceptance of the algorithm in part 1. Evaluate $M$ that maximizes the probabilty of acceptance in case of $\alpha=2$ and $\beta=2$. Implement the algorithm of part 1 with this value of $M$ and estimate the acceptance probability.

3. An alternative method of generating a Beta random variable is to generate two independent random variables $U$ and $V$ from Unif$[0,1]$, and take ${U^{1/\alpha}}/(U^{1/\alpha}+V^{1\beta})$ only when $U^{1/\alpha}+V^{1/\beta} \le 1$. Evaluate the probability of acceptance of this strategy when $\alpha=\beta=2$. Compare your result with that of part 2. Implement this method and estimate the acceptance probability.
-->

<!--
## Q2. Acceptance-rejection sampling

The Gamma distribution with shape parameter $\alpha$ and scale parameter $1$ has density proportional to
$$
	\tilde{f}(x) = \begin{cases}
			x^{\alpha-1}e^{-x}, & x > 0 \\
			0, & \text{otherwise}.
	\end{cases}
$$

1. \item (30 pts) Show that, for $\alpha > 1$, 
$$
	g(x) = \frac{(\alpha-1)^{\alpha-1}e^{-(\alpha-1)}}{1 + [x - (\alpha - 1)]^2/(2\alpha - 1)}
$$
dominates $\tilde{f}(x)$, i.e., $g(x) \ge \tilde{f}(x)$ for all $x$.
(\emph{Hint}. $\frac{d}{dx}\left(x^{\alpha-1}e^{-x}(2\alpha - 1 + [x - (\alpha - 1)]^2)\right) = -x^{\alpha-2}e^{-x}(x - \alpha)^2[x - (\alpha - 1)]$.)

2. Propose an algorithm that generate a $\text{Gamma}(\alpha, 1)$ random number for a given $\alpha > 1$.

3. Implement your algorithm and test.
-->

## Q2. Random number generator

1. Write a linear congruential generator
$$
\begin{split}
    x_{i+1} &= (a x_i + c) \mod m, \quad i=1, 2, \dotsc \\
    u_i &= x_i / m.
\end{split}
$$
for $m = 2^{32}$, $a = 1103515245$, $c = 12345$, and for $m = 2048$, $a = 1229$, $c = 1$ respectively. Compare the two random number generators.

2. In case the inverse CDF $F^{-1}$ is not exclicitly available, can you implement the inverse CDF method for random number generation? Assume that the pdf of the distribution exists. Implement your method.


## Q3. Acceptance-rejection sampling
As an alternative to the Box-Muller or Marsaglia method, consider the following method of sampling a normal random variable using the absolute value $X=|Z|$ of a standard normal random variable $Z$.
1. Find the probability density function $f_X$ of $X$.
2. If $g$ is the probability density function of an exponential random variable with mean $1$, find the smallest $c > 0$ such that
	$$
		\frac{f_X(x)}{g(x)} \le c, \quad \text{for all } x > 0.
	$$
3. Propose an algorithm that generate $X$, the absolute value of the standard normal random variable $Z$.
4. How would you generate $Z$?
5. Implement your algorithm and test.
6. How efficient is your algorithm?

## Q4. Importance sampling

Consider testing the hypotheses $H_0: \lambda=2$ versus $H_a: \lambda>2$ using 25 observations from a Poisson($\lambda$) model. Rote application of the central limit theorem would suggest rejecting $H_0$ at $\alpha=0.05$ when $Z > 1.645$, where $Z = \frac{\bar{X}-2}{\sqrt{2/25}}$.

1. Estimate the size of this test (i.e., the type I error rate) using three Monte Carlo approaches: standard, antithetic, (unstandardized) importance sampling. Provide a confidence interval for each estimate. Discuss the relative merits of each variance reduction technique.
	
	For the importance sampling approach, use a Poisson envelope ($h$ in the course notes) with mean equal to the $H_0$ rejection threshold, namely $\lambda = 2.4653$. 
    
2. Draw the power curve for this test for $\lambda \in [2.2,4]$, using the same three techniques. Provide pointwise confidence bands in each case. Discuss the relative merits of each technique in this setting. 

