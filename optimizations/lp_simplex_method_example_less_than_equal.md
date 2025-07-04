---
layout: default
title: "Linear Programming: Maximization with Simplex Method (≤ constraints)"
---

IMPORTANT: This is a specific and significantly simple maximization problem with containing only ≤ constraints to create a beginner-friendly explanation. Other conditions require different method so please be aware when following this explanation.

$$\text{Maximize:} \space z = 8x_1 + 12x_2$$

$$\text{subject to:}
- 2x_1 + 4x_2 \le 6
- x_1 + 3x_2 \le 4
- x_1, x_2 \ge 0
$$

1. Let’s explore the problem:
    - targeting a maximization
    - every constraint is less-than-equal inequality
    - every decision variable is non-negative
2. Before applying the Simplex Method, the following conditions should be satisfied:
    - the linear program should be in *standard form* (for this type of maximization problem, not in general)
        - maximization program
        - all constraints are written as equalities (using slack or surplus variables)
        - all decision variables are restricted to be non-negative
        
        → Since the problem already satisfies the first and third requirement, we should work on the second requirement. This will be shown at the next step.
        
    - all right-hand-side (RHS) of constraints should be non-negative
        
        → We have 6 and 4 as a right-hand-side for constraints, we satisfy this requirement.
        
    - a basic feasible solution (bfs) must exist before starting the Simplex Method
        
        → This requirement will also be shown at the next step.
        
3. Let’s set up the spec to apply a Simplex Method requirements:
    - since inequalities are in less-than-equal format, we add slack variables to convert them into equalities:
        - $2x_1 + 4x_2 + x_3 = 6, \space \text{where:} \space x_3 \ge 0$
        - $x_1 + 3x_2 + x_4 = 4, \space \text{where:} \space x_4 \ge 0$
        
        → now, constraints are all having an equality.
        
    - we should check a basic feasible solution existing by setting $x_1, x_2 = 0$
        - $2(0) + 4(0) + x_3 = 6 → x_3 = 6$
        - $(0) + 3(0) + x_4 = 4 → x_4 = 4$
        
        → since we get $x_3 = 6$ and $x_4 = 4$, initial basic feasible solutions exist.
        
    - the objective function $z$ should be re-written to fit into our tableau — makes more straightforward to track how the objective function changes as we pivot:
        - $z = 8x_1 + 12x_2 → z - 8x_1 - 12x_2 = 0$
4. Now we’re all set to generate a tableau:

| **Basis** | $x_1$ | $x_2$ | $x_3$ | $x_4$ | $\text{RHS}$ |
| --- | --- | --- | --- | --- | --- |
| $x_3$ | 2 | 4 | 1 | 0 | 6 |
| $x_4$ | 1 | 3 | 0 | 1 | 4 |
| $z$ | -8 | -12 | 0 | 0 | 0 |

⚠️ **Work in Progress:** This note is not yet complete. Please check back later.

---
This summary is based on *Linear Programming Notes* [https://math.mit.edu/~goemans/18310S15/lpnotes310.pdf] by Michel Goemans, MIT