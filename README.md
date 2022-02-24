# M1399.000100 Computational Statistics @ SNU 2021

This is the course website for M1399.000100: "Computational Statistics" at Seoul National University in Spring 2021. Assignments, lecture notes, and open source code will all be available on this website.

## Announcements

- 2021-05-28: Homework 4 has been posted.
- 2021-05-22: Homework 3 deadline has been extended to 2021-05-26
- 2021-04-14: Lecture notes for "iterative methods for linear systems" has been updated.
- 2021-04-14: Hint for Homework 2 Q3-4 has been revised.

## Instructor 

Joong-Ho (Johann) Won

**Email**: wonj AT stats DOT snu DOT ac DOT kr

**Class Time**: Mondays/Wednesdays 15:30 - 16:45 @ online

**Office Hours**: By appointment.

**Textbook**: 
- 심송용. 통계계산. 교문사, 2006. 


**References**: 
- G.H. Givens and J.A. Hoeting. Computational Statistics (2ed). Wiley, 2013. 
- N. Matloff. The Art of R Programming. No Starch Press, 2011. 

	
## Course Objectives

최근 수십년 간의 컴퓨터 기술의 발전으로 인해 이전에는 쉽게 상상할 수 없었던 복잡한 통계모형들을 통계분석에서 실제로 사용할 수 있게 되었다. 따라서 현대의 복잡하고 다양한 통계모형들을 사용하기 위해서는 컴퓨터를 이용한 여러 가지 통계계산 방법들을 습득하는 것이 필수불가결한 과제가 되었다. 이 과목에서는 모수론적 통계와 베이지안 통계에 필요한 통계계산 방법들을 배우고 이를 실제 컴퓨터로 구현해 보는 것을 목표로 한다. 이 과목에서 배우는 내용은 크게 다음과 같다.

* 우도함수의 최적화 방법 – 행렬방정식의 수치적 해법, 최소제곱법, 비선형방정식 

* 수치적분 – 결정론적 및 몬테카를로 방법

* 분포함수로부터의 난수 생성 


## Course Overview

### Assessment

The course will be graded based on the following components:

- **Attendance** (4%): Mandatory.
- **Assignments** (46%): You will be assigned 4 homework assignments to be completed using R regularly throughout class. 
- **Final exam** (50%): tentatively scheduled on 6/9 (Wed)

### Schedule

The following schedule is tentative, and is subject to change over the course.

| Week | Topic | Textbook Chapter | Assignment | Due Date |
|---| --- | --- | --- | --- | 
| 1 (3/2)           | Computer Arithmetic [[notebook](./lectures/lecture1/arith.ipynb)] [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture1%2Farith.ipynb) | - | [Homework 1](./homework/hw1.md) | 2021-03-28 | 
| 2 (3/8, 3/10)     | Computer Arithmetic | - |  |  |
| 3 (3/15, 3/17)    | Direct methods for linear systems: LU decomposition [[notebook](./lectures/lecture2/gelu.ipynb)] [[example](./lectures/lecture2/gelu.pdf)] [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture2%2Fgelu.ipynb) | 2장 |  |  |
| 4 (3/22, 3/24)    | Direct methods for linear systems: LU decomposition | 2장 |  |  |
| 5 (3/29, 3/31)    | Direct methods for linear systems: Cholesky decomposition [[notebook](./lectures/lecture3/chol.ipynb)] [![binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/m1399_000100-2021spring/HEAD?filepath=lectures%2flecture3%2fchol.ipynb) | 2장 | [Homework 2](./homework/hw2.md) [[pdf]](./homework/hw2.pdf) | 2021-04-25 |
| 6 (4/5, 4/7)      | Direct methods for least squares: QR decomposition [[notebook](./lectures/lecture4/qr.ipynb)] [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture4%2Fqr.ipynb) | 6장 |  |  |
| 7 (4/12, 4/14)    | Iterative methods for linear systems [[notebook]](./lectures/lecture5/iterative.ipynb) [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture5%2Fiterative.ipynb) | 6장 |  |  |
| 8 (4/19, 4/21)    | Iterative methods for linear systems | 3장 |  |  |
| 9 (4/26, 4/28)    | Solving nonlinear equations [[notebook]](./lectures/lecture6/nonlinear.ipynb) [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture6%2Fnonlinear.ipynb) | 3장| [Homework 3](./homework/hw3.md) [[pdf]](./homework/hw3.pdf)   | ~~2021-05-23~~ 2021-05-26 |
| 10 (5/3)   | Optimization [[notebook]](./lectures/lecture7/optim.ipynb) [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture7%2Foptim.ipynb)  | 4장 |  |   |
| 11 (5/10, 5/12)   | Optimization | 4장 |  |  |
| 12 (5/17)         | Numerical integration [[notebook]](./lectures/lecture8/integration.ipynb) [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture8%2Fintegration.ipynb) | - |  |  |
| 13 (5/24, 5/26)   | Random number generation [[notebook]](./lectures/lecture9/rng.ipynb) [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture9%2Frng.ipynb) | 8장 | [Homework 4](./homework/hw4.md) [[pdf]](./homework/hw4.pdf) | 2021-06-13 |
| 14 (5/31, 6/2)    | Monte Carlo integration [[notebook]](./lectures/lecture10/mc.ipynb) [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/won-j/M1399_000100-2021spring/HEAD?filepath=lectures%2Flecture10%2Fmc.ipynb) | 9장 |  |  |
| 15 (6/7, 6/9)     | Monte Carlo integration          |  |  |  |
| 16 (6/14)         | Final Exam      |  |  |  |


