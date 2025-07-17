---
layout: default
title: "Linear Programming: Standard Form Requirements for the Simplex Method"
---

To apply the Simplex Method, a linear program must be converted into standard form, which satisfies the following conditions:

1. Objective function ($z$) must be a maximization:
    - If the original problem focus on minimization, multiply objective function by $-1$
        
        $$
        \text{min} \ z = c^{T}x ⇒ \text{max} \ z = -c^{T}x
        $$
        
2. Every constraint must be equalities:
    - $≤$ constraint: add a slack variable $s_j$, where $s_j ≥ 0$
        
        $$
        a^{T}x \le b ⇒ a^{T}x + s_j = b
        $$
        
    - $≥$ constraint: subtract a surplus variable $\bar{s_j}$ and add an artificial variable $a_j$, where $\bar{s_j}, a_j ≥ 0$
        
        $$
        a^{T}x \ge b ⇒ a^{T}x - \bar{s_j} + a_j = b
        $$
        
    - $=$ constraint: add an artificial variable $a_j$, where $a_j ≥ 0$
        
        $$
        a^{T}x = b ⇒ a^{T}x + a_j = b
        $$
        
3. Each constraint’s right-hand-side must be non-negative:
    - If the right-hand-side of a constraint is negative, multiply the entire constraint by $-1$ and flip the inequality sign if needed.
4. All decision variables must be non-negative:
    - Every decision variable must satisfy the non-negativity
        
        $$
        x_1,x_2,...,x_n \ge 0
        $$
        
    - If any decision variable is unrestricted in sign, replace it with the difference of two non-negative variables
        
        $$
        x_j = x_j^{+} - x_j^{-}, \quad\text{where} \space x_j^{+},x_j^{-} \ge 0
        $$

---
Summary inspired by *Introduction to Operations Research* by Hillier and Lieberman.