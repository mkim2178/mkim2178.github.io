---
layout: default
title: "Linear Programming: A Highly Simplified Example of the Simplex Method"
---

This is a very simple example of applying simplex method to the linear program. Note that it does not include a detailed explanation.

Maximize:

- $z=8x_1+12x_2$

subject to:

- $2x_1+4x_2 \le 6$
- $x_1+3x_2 \le 4$

Rewrite the objective function $z$:

$z - 8x_1 - 12x_2 = 0$

Add slack variables $(x_3, x_4)$ to inequalities to convert them into equalities:

- $2x_1+4x_2+x_3=6$
- $x_1+3x_2+x_4=4$
- $x_1, x_2, x_3, x_4 \ge 0$
- $\text{basis variables:} \space B = \{x_3, x_4\}$

Create a Tableau:

| Variable     |&nbsp;$z$ |  &nbsp;$x_1$ |  &nbsp;$x_2$|  &nbsp;$x_3$ |  &nbsp;$x_4$ |  &nbsp;RHS |
|:--------------------|-------:|-------:|-------:|-------:|-------:|-----:|
| **Cost Coefficients** |      1 |     -8 |    -12 |      0 |      0 |   0 |
| **Row 1**         |      0 |      2 |      4 |      1 |      0 |    6 |
| **Row 2**         |      0 |      1 |      3 |      0 |      1 |    4 |

We start from the variable that has the lowest cost coefficient (since we want to take a huge step to efficiently (and instantly) reach the maximum, we should select the variable with the most negative reduced cost coefficient to enter the basis):

$\text{entering basis:} \space x_2$

Compute each of the quotient from $\text{row 1}$ and $\text{row 2}$ by using the minimum ratio test:

$$
q_1 = \frac{\text{RHS of Row 1}}{\text{cost coefficient of x₂ from Row 1}} = \frac{6}{4}
$$

$$
q_2 = \frac{\text{RHS of Row 2}}{\text{cost coefficient of x₂ from Row 2}} = \frac{4}{3}
$$

Since $q_1 \gt q_2$, our departing basis will be $x_4$

⚠️ **Work in Progress:** This note is not yet complete. Please check back later.

---
This summary is based on *Linear Programming Notes* [https://math.mit.edu/~goemans/18310S15/lpnotes310.pdf] by Michel Goemans, MIT