---
 title: "Homework 3"
 author: "M1399.000100, Seoul National University, Spring 2021"
 date: "Due 23:59 Sunday, 2021-05-23"
 output: html_document
---

# M1399.0001000 Homework 3, Spring 2021, Seoul National University
~~Due 23:59 2021-05-23~~
Due 23:59 2021-05-26

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


## Q2. Optimization

1. In the lecture note on optimization, we used step-halving in the Fisher scoring of the Poisson regression analysis of the quarterly count data of AIDS deaths in Australia. Repeat this using the Armijo rule.

1. In the sa,me lecture note, it is stated that Poisson regression has the objective function $f(\beta) = -\sum_{i=1}^n \left[ y_i \mathbf{x}_i^T \beta - \exp(\mathbf{x}_i^T \beta) - \log(y_i!) \right]$ and its gradient
\begin{align*}
	\nabla f(\beta) &= -\sum_{i=1}^n \left( y_i \mathbf{x}_i - \exp(\mathbf{x}_i^T \beta)\mathbf{x}_i \right) \\
	&= -\sum_{i=1}^n (y_i - \lambda_i) \mathbf{x}_i = -\mathbf{X}^T (\mathbf{y} - \boldsymbol{\lambda})
\end{align*}
is *not* Lipschitz continuous. Show this.

## Q3. IRLS

1. A researcher is interested in how variables, such as GRE (Graduate Record Exam scores), GPA (grade point average) and prestige of the undergraduate institution, effect admission into graduate school. The response variable, admit/don’t admit, is a binary variable.
\    
The data is available at <https://stats.idre.ucla.edu/stat/data/binary.csv>. How to analyze these data can be found in the website <https://stats.idre.ucla.edu/r/dae/logit-regression/>.
\    
Implement the iteratively reweighted least squares (IRLS) algorithm for fitting a logistic regression model, and apply your algorithm to the admission data above. Compare your result with that of 
```r
    glm(admit ~ gre + gpa + rank, data = mydata, family = "binomial")
```
Note that the variable `rank` is categorical data.


## Q4. Newton-Côtes quadrature

1. Write functions `rectangular()`, `trapezoidal()`, and `simpson()`, which evaluates the integral of a given mathematical function taking a single `numeric` argument and returns a `numeric`, using the Riemann rule, the trapezoidal rule, and Simpson's rule, respectively. An example of the function that takes a single `numeric` argument and returns a `numeric` is the R builtin function `exp()`. The three functions should share the same signature: in addition to the integrand, they should take the start and the end points of the interval of integration, and the number of points in subdivision, returning the value of the integral.

2. Write a function `integral(f, a, b, n, method)` that evaluates the integral of function `f` from `a` to `b` using `n`-point subdivision and numerical integration method `method`. The value of `method` can be either `rectangular`, `trapezoidal`, or `simpson`. Your implementation **must not use `switch`**. Instead, use function objects. Write two versions of each function so that one uses `for` (or `while`) loop and the other vectorizes as many as computation as possible. Put your loopy functions in `integral_loops.R` and vectorized functions in `integral_vec.R`.

3. Use your function to evaluate $\int_0^2 e^{-x}dx$ and discuss its accuracy.

4. Use your function to evaluate $\int_1^{\infty}e^{-x}x^{-1/2}dx$. Note the length of the integration interval is infinite. Use the transformation $t=1/x$ to make the interval finite. Despite of this change of variable, there remains a problem. Specify what it is and how you solved this problem.

## Q5. Gauss-Hermite quadrature

1. Suppose $y_1, \dotsc, y_n$ are a random sample from a Poisson distribution with mean $\lambda=\exp(\alpha)$. Suppose the prior on $\alpha$ is $\mathcal{N}(0,100)$. The observed data are
$$
11, 19, 27, 12, 14, 11, 10, 13, 15, 10.
$$
Use Gauss-Hermite quadrature to evaluate the mean and variance of the posterior distribution of $\alpha$. Remember to make a change of variables in the integeral, if appropriate, before applying the quadrature formaulas. Give some discussion of the accuracy of these calculations. Use the function `guass.quad()` available in the R package `statmod`.

