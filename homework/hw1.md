---
 title: "Homework 1"
 author: "M1399.000100, Seoul National University, Spring 2021"
 date: "Due 23:59 Sunday, 2021-03-28"
 output: html_document
---

# M1399.0001000 Homework 1, Spring 2021, Seoul National University
Due 23:59 2021-03-28

#### **No late submission is accepted**. 


## Q1. Textbook Problems

1. 심송용, 제 1장 연습문제 1.4, 1.6, 1.8.
1. 심송용, 제 2장 연습문제 2.1, 2.2.


## Q2. Floating point

1. R uses the IEEE 754 double precision in most of the platforms. 
    + What is the number of significant digits (in base 2) for R `double`? 
    + Denote your answer to part (a) by $p$. What is the next representative number larger than 1?
    + We want to find the smallest number that added to 1 will give a result different from 1 (i.e., $\epsilon_{\max}$). Try adding $1/2^p$ to 1. Provide your R code and the result. Set the number of decimal digits to be displayed to 20 using \texttt{options(digits=20)}.
    + Find $\epsilon_{\max}$ and verify $1+\epsilon_{\max}$ does give a value different from 1. Provide your R code and the result.
    + Repeat all of the above for IEEE 754 single precision floating point numbers. (*Hint*. Use the package `float`.)

1. In R, let `a <- 0.7`, `b <- 0.2`, and `c <- 0.1`. Make sure setting `options(digits=20)`.
    + Test whether `(a + b) + c` equals 1. 
    + Test whether `a + (b + c)` equals 1. 
    + Test whether `(a + c) + b.` equals 1.
    + Explain what you found.(*Hint* find the internal representation of these numbers).

## Q3. Numerical precision

Consider the evaluation of $e^x$ using the Taylor series
$$
    e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \dotsb
$$
in R. Write function `expTaylor()` that takes a double-precision floating point number `x` and executes the following.
```R
	stop <- 100
	ex <- 1
	xi <- 1
	ifac <- 1
	for (i in 1:stop) {
		xi <- xi * x
		ifac <- ifac * i
		ex <- ex + xi / ifac
	}
	ex
```

Now let `x <- 20.0`. A correct implementation of `expTaylor()` should yield `485165195.40979015827` (with `options(digits=20)`, which is close enough to `485165195.40979027748` that the built-in fuction `exp()` yields.

1. Compare the values of `expTaylor(-20.0)` and `1 / expTaylor(20.0)`. Calculate the relative error of the two values, assuming that `exp(-20.0)` is the true value. Explain what you found.

1. We can think of the algorithm given in the R code above as an iterative algorithm in `i`. At each value of `i`, there is a difference in the value of ex and the true value `ex`. (The exact value of this difference is the truncation error.) Modify the code (or use different code) to determine the relative error in `ex` for each value of `i`. For `x = 20.0`, make a plot of the relative error and the number of iterations (that is, of `i`) for 1 to 100 iterations. Now, repeat this for `x = −20.0`. Explain what you found.

1. Determine the order of the error for approximating `ex` with the Taylor series for `x = 20` in terms of the number of iterations (that is, the number of terms in the Taylor series).

		
## Q4. Rcpp

1. In class, we used the following function
	```r
	Rcpp::cppFunction('int float32bin(double x) {
    	float flx = (float) x; 
    	unsigned int binx = *((unsigned int*)&flx); 
    	return binx; 
	}')
	```
to inspect single-precision floating point numbers. 
Figure out and explain what the included C++ code does.

## Q5. Triangular systems

Show the following facts about triangular matrices. A unit triangular matrix is a triangular matrix with all diagonal entries being 1.

1. The product of two upper (lower) triangular matrices is upper (lower) triangular.

2. The inverse of an upper (lower) triangular matrix is upper (lower) triangular.

3. The product of two unit upper (lower) triangular matrices is unit upper (lower) triangular.

4. The inverse of a unit upper (lower) triangular matrix is unit upper (lower) triangular.

5. An orthogonal upper (lower) triangular matrix is diagonal.

