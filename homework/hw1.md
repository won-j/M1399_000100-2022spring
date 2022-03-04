---
 title: "Homework 1"
 author: "M1399.000100, Seoul National University, Spring 2022"
 date: "Due 23:59 Sunday, 2022-03-27"
 output: html_document
---

# M1399.0001000 Homework 1, Spring 2022, Seoul National University
Due 23:59 2022-03-27

#### **No late submission is accepted**. 


## Q1. Textbook Problems

1. 심송용, 제 2장 연습문제 2.1, 2.2, 2.3.


## Q2. Floating point

1. In the IEEE 754 single precision format, what is the bitstring of the fractional part (mantissa) of the decimal number 0.110 in the default rounding mode, rounding to nearest, ties to even?

1. In the field of reals, the identity element $a$ of addition satisfies the following three conditions.
    + $a = 0$ is unique.
    + $a + x = x$ for any $x$. 
    + $x − x = a$ for any $x$.
Are these conditions hold for the system of floating point numbers? Discuss.

1. Write an R program that computes
$$
    \sum_{i=1}^{\infty}i
    .
$$
Will the computations overflow? If so, approximately at what value of `i`? Or will the series converge? If so, to what value, and approximately at what value of `i`? Explain the observed behavior of R in terms of the parameters of the IEEE 754 standard.

1. Answer the same questions as above, but for
$$
    \sum_{i=1}^{\infty}\frac{1}{i}
    .
$$


## Q3. Numerical precision

Consider the evaluation of $e^x$ using the Taylor series
$$
    e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \dotsb
$$
in R. Write function `expTaylor()` that takes a double-precision floating point number `x` and executes the following.

```
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

```
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

