---
 title: "Homework 3"
 author: "M1399.000100, Seoul National University, Spring 2022"
 date: "Due 23:59 Sunday, 2022-05-25"
 output: html_document
---

# M1399.0001000 Homework 3, Spring 2022, Seoul National University
Due 23:59 2022-05-25

#### **No late submission is accepted**. 

## Q1. Contraction map

Recall that function $F: [a,b] \rightarrow [a,b]$ is contractive if there exists a nonnegative constant $L<1$ such that
$$
|F(x) - F(y)| \le L |x-y|  
\tag{Lip}
$$
for all $x,y \in [a,b]$.


1. Show that if $F$ is differentiable on $[a,b]$, then condtion (Lip) is equivalent to
	$$
	|F'(x) | \le L
	$$
	for all $x \in [a,b]$.

Now suppose we want to find a root of a differentiable function $f(x)$ on $(a,b)$. Consider the following iteration
$$
	x^{(t+1)} = x^{(t)} + \alpha  f(x^{(t)}) \quad (\alpha \neq 0).
    \tag{Iter}
$$

2. When does iteration (Iter) converge?
3. Discuss the advantage of introducing the $\alpha$.
4. Relate iteration (Iter) with the gradient descent method for minimization of a twice differentiable function.


## Q2. Poisson regression

1. In the lecture note on optimization, we used step-halving in the Fisher scoring of the Poisson regression analysis of the quarterly count data of AIDS deaths in Australia. Repeat this using the Armijo rule.

1. In the same lecture note, it is stated that Poisson regression has the objective function $f(\beta) = -\sum_{i=1}^n \left[ y_i \mathbf{x}_i^T \beta - \exp(\mathbf{x}_i^T \beta) - \log(y_i!) \right]$ and its gradient
\begin{align*}
	\nabla f(\beta) &= -\sum_{i=1}^n \left( y_i \mathbf{x}_i - \exp(\mathbf{x}_i^T \beta)\mathbf{x}_i \right) \\
	&= -\sum_{i=1}^n (y_i - \lambda_i) \mathbf{x}_i = -\mathbf{X}^T (\mathbf{y} - \boldsymbol{\lambda})
\end{align*}
is *not* Lipschitz continuous. Show this.

## Q3. Gradient descent

1. In $K$-class logistic regression, we observe $n$ independent categorical variables with $K > 2$ categories, each associated with covariates. Let $\mathbf{y}_i$ be the $i$th observation and $\mathbf{x}_i \in \mathbf{R}^p$ be the associated covariate vector. We use a dummy variable encoding for the response so that $\mathbf{y}_i$ is a $K$-dimensional binary vector with only one component being 1. Let $p_k$ be the probability of the $k$th category. We want to model the logit transform of $p_k$ as a linear function of the covariate $\mathbf{x}_i$.
	Due to the constraint $\sum_{k=1}^K p_k = 1$, we set
$$
	\log\frac{p_k}{p_K} = \mathbf{x}_i^T\boldsymbol{\beta}_k
	,
	\quad
	k = 1, \dotsc, K - 1
$$
and $\boldsymbol{\beta}_K = 0$.
\
    a. Express the log likelihood of the data in terms of the matrices $\mathbf{Y} = (y_{ik}) \in \mathbb{R}^{n \times K}$ and $\mathbf{X} = [\mathbf{x}_1, \dotsc, \mathbf{x}_n]^T$ or their components. You may ignore terms irrelevant to $\boldsymbol{\beta}_k$.
    b. Write down a gradient ascent step for estimating coefficients $\mathbf{B} = [\boldsymbol{\beta}_1, \dotsc, \boldsymbol{\beta}_{K-1}]$.


## Q4. IRLS

1. A researcher is interested in how variables, such as GRE (Graduate Record Exam scores), GPA (grade point average) and prestige of the undergraduate institution, effect admission into graduate school. The response variable, admit/don’t admit, is a binary variable.
\    
The data is available at <https://stats.idre.ucla.edu/stat/data/binary.csv>. How to analyze these data can be found in the website <https://stats.idre.ucla.edu/r/dae/logit-regression/>.
\    
Implement the iteratively reweighted least squares (IRLS) algorithm for fitting a logistic regression model, and apply your algorithm to the admission data above. Compare your result with that of 
```r
    glm(admit ~ gre + gpa + rank, data = mydata, family = "binomial")
```
Note that the variable `rank` is categorical data.


## Q5. Newton-Côtes quadrature

1. Write functions `rectangular()`, `trapezoidal()`, and `simpson()`, which evaluates the integral of a given mathematical function taking a single `numeric` argument and returns a `numeric`, using the Riemann rule, the trapezoidal rule, and Simpson's rule, respectively. An example of the function that takes a single `numeric` argument and returns a `numeric` is the R builtin function `exp()`. The three functions should share the same signature: in addition to the integrand, they should take the start and the end points of the interval of integration, and the number of points in subdivision, returning the value of the integral.

2. Write a function `integral(f, a, b, n, method)` that evaluates the integral of function `f` from `a` to `b` using `n`-point subdivision and numerical integration method `method`. The value of `method` can be either `rectangular`, `trapezoidal`, or `simpson`. Your implementation **must not use `switch`**. Instead, use function objects. Write two versions of each function so that one uses `for` (or `while`) loop and the other vectorizes as many as computation as possible. Put your loopy functions in `integral_loops.R` and vectorized functions in `integral_vec.R`.

3. Use your function to evaluate $\int_0^2 e^{-x}dx$ and discuss its accuracy.

4. Use your function to evaluate $\int_1^{\infty}e^{-x}x^{-1/2}dx$. Note the length of the integration interval is infinite. Use the transformation $t=1/x$ to make the interval finite. Despite of this change of variable, there remains a problem. Specify what it is and how you solved this problem.

## Q6. Gauss-Hermite quadrature

1. Suppose $f$ is a continuous (real-valued) function defined on the interval $[a, b]$. 
		Weierstrass Approximation Theorem states that, for every $\epsilon > 0$, there exists a polynomial $p$ such that $|f(x) - p(x)| < \epsilon$  for all $x$ in $[a, b]$.
%
Also suppose $w$ is a density function concentrated on $[a, b]$.
Let
$$
	Q_n(f) = \sum_{i=0}^{n-1} A_i^{(n)}f(x_i^{(n)})
$$
be the sequence of Gaussian quadrature of order $n$ applied to $f$, based on the sequence of $w$-orthogonal polynomials $\bar{q}_n(x)$.
%
Show that
$$
	\lim_{n\to\infty}Q_n(f) = E[f(X)]
	%\int_a^b f(x)w(x)dx
	,
$$
where $X$ is a random variable whose distribution has density $w$.

1. Suppose $y_1, \dotsc, y_n$ are a random sample from a Poisson distribution with mean $\lambda=\exp(\alpha)$. Suppose the prior on $\alpha$ is $\mathcal{N}(0,100)$. The observed data are
$$
11, 19, 27, 12, 14, 11, 10, 13, 15, 10.
$$
Use Gauss-Hermite quadrature to evaluate the mean and variance of the posterior distribution of $\alpha$. Remember to make a change of variables in the integeral, if appropriate, before applying the quadrature formaulas. Give some discussion of the accuracy of these calculations. Use the function `guass.quad()` available in the R package `statmod`.

