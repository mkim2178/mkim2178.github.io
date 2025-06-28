---
layout: default
title: "Linear Programming: Formations and Transformations"
---
How can we represent linear Programs?

Linear programs can be expressed in various forms depending on the structure of the problem. However, to maintain consistency and simplify the solving process, any linear program can be converted into a *standard form*.

A linear program can be expressed in different formations.
- The objective function may involve maximizing or minimizing a linear expression, depending on the context of the problem.
- The constraints, which restrict the decision variables, can be equalities or inequalities.
- The decision variables may be non-negative or unrestricted in sign.

To simplify the solving process, a linear program can be converted into a standard form:
- The objective function is written as a maximization.
- Every constraint is expressed as an equality.
- Every decision variable satisfies non-negativity.

Matrix form of a standard-formed linear program:
    
- Maximize: $z = c^{T}x$

- subject to:
    - $Ax = b$
    - $x \ge 0$

    where

    $$
    c=\begin{pmatrix} c_1\\ \vdots \\ c_n \end{pmatrix},
    b=\begin{pmatrix} b_1\\ \vdots \\ b_m \end{pmatrix},
    x=\begin{pmatrix} x_1\\ \vdots \\ x_n \end{pmatrix}
    $$

    are column vectors,

- $c^{T}$: a transpose of vector $c$
- $A=[a_{ij}]$: $m \times n$ coefficient matrix

Every linear program can be transformed into a standard form using the following techniques:

- A minimization objective can be converted to a maximization objective by negating it:

$$
\text{Minimize:}\space z=c_1x_1 + \cdots + c_nx_n

\text{Maximize:}\space z'= -z = -c_1x_1-\cdots-c_nx_n
$$

- An inequality constraint of the form:

    $$
    a_{i1}x_1+\cdots+a_{in}x_n \le b_i
    $$

    can be converted into an equality by adding a nonnegative *slack* variable $s$ to convert it to an equality constraint:

$$
a_{i1}x_1+\cdots+a_{in}x_n + s = b_i, \space s \ge 0
$$
    
- An inequality constraint of the form:

    $$
    a_{i1}x_1+\cdots+a_{in}x_n \ge b_i
    $$
        
    can be converted into an equality by subtracting a nonnegative *surplus* variable $s$ to convert it to an equality constraint:
    
$$
a_{i1}x_1+\cdots+a_{in}x_n-s=b_i,\space s \ge 0
$$
    
- If a decision variable $x_j$ is unrestricted in sign, it can be replaced by difference of two non-negative variables:
        
$$
x_j = x_j^{+}-x_j^{-},\space \text{where} \space x_j^{+} \ge 0, \space x_j^{-} \ge 0
$$

---
Based on lecture notes by Michel Goemans for MIT 18.310A ([MIT OCW link](https://ocw.mit.edu/courses/18-310-principles-of-discrete-applied-mathematics-fall-2013/resources/mit18_310f13_ch8/)), licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).