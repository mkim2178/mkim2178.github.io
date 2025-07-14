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

4. Now we’re all set to convert the linear program into a tableau format:

    | **Basis** | $x_1$ | $x_2$ | $x_3$ | $x_4$ | **RHS** |
    |:---------:|:-----:|:-----:|:-----:|:-----:|:-------:|
    |   $x_3$   |   $2$   |   $4$   |   $1$   |   $0$   |    $6$    |
    |   $x_4$   |   $1$   |   $3$   |   $0$   |   $1$   |    $4$    |
    |    $z$    |  $-8$   | $-12$   |   $0$   |   $0$   |    $0$    |

    - Let B is the set of basis: $B = {x_3, x_4}$
    - Let N is the set of non-basis: $N = {x_1, x_2}$

5. At this moment, we will start the iteration of computation of Simplex Method and will update the entering and leaving variables.

    **Iteration 1:**

    1. First, we have to find the pivot column. Since we want to maximize, we look for the most negative reduced cost. This indicates the non-basic variable whose increase will most improve $z$. From this example, our pivot column will be the second column, where the non-basic element $x_2$ is located.

    2. Next, we should select the pivot row. To select the pivot row, we should compare quotients that are created by the minimum ratio test from each row (**note that only ratios with positive denominators are considered!**):

        $$
        \text{minimum ratio test:} \space \frac{\text{RHS}}{\text{pivot column coefficient}}
        $$

        - $\frac{6}{4} = 1.5$
        - $\frac{4}{3} \approx 1.3$
    
    3. Since $\frac{6}{4} > \frac{4}{3}$, our pivot row will be row 2 because we should select the row that has the smallest quotient (the main purpose of this example is we should increase the value of the objective function so we need the element that has the smallest quotient)

    4. Now, we can select the pivot element which is the intersection of pivot column and row. We can now determine our new entering and leaving variables in current iteration and update our basis $B$:

        - We should make our pivot element to 1 so we’re pivoting correctly (we divide our pivot row with 3):
            - $\frac{1}{3}x_1 + x_2 + \frac{1}{3}x_4 = \frac{4}{3}$

        - We should re-write the other rows with our new $x_2$ where $x_2 = \frac{4}{3} - \frac{1}{3}x_1 - \frac{1}{3}x_4$:

            $$
            \begin{aligned}
            2x_1 + 4x_2 + x_3 &= 6 \\
            2x_1 + 4\left(\frac{4}{3} - \frac{1}{3}x_1 - \frac{1}{3}x_4\right) + x_3 &= 6 \\
            2x_1 + \frac{16}{3} - \frac{4}{3}x_1 - \frac{4}{3}x_4 + x_3 &= 6 \\
            \frac{2}{3}x_1 + x_3 - \frac{4}{3}x_4 &= \frac{2}{3} \quad \text{(new row 1)}
            \end{aligned}
            $$

        - We also have to re-write the $z$ with our new $x_2$:

            $$
            \begin{aligned}
            z - 8x_1 - 12x_2 &= 0 \\
            z - 8x_1 - 12\left(\frac{4}{3} - \frac{1}{3}x_1 - \frac{1}{3}x_4\right) &= 0 \\
            z - 8x_1 - 16 + 4x_1 + 4x_4 &= 0 \\
            z - 4x_1 + 4x_4 &= 16 \quad \text{(new z)}
            \end{aligned}
            $$

        - At this moment, our $x_2$, is the new **entering variable** (our new basic variable). Since our $x_4$ has been replaced, this is determined as a **leaving variable** (our new non-basic variable)

        - Let’s update our tableau:

            | **Basis** |  $x_1$  | $x_2$ | $x_3$ |   $x_4$   |  **RHS**  |
            |:---------:|:-------:|:-----:|:-----:|:---------:|:---------:|
            |   $x_3$   |  $\frac{2}{3}$  |   $0$   |   $1$   |  $-\frac{4}{3}$  |  $\frac{2}{3}$  |
            |   $x_2$   |  $\frac{1}{3}$  |   $1$   |   $0$   |  $\frac{1}{3}$   |  $\frac{4}{3}$  |
            |    $z$    |    $-4$   |   $0$   |   $0$   |     $4$     |    $16$     |

            $$
            \begin{aligned}
            \text{Basis}: \space B &= \{ x_3, x_2 \} \\
            \text{Non-Basis}: \space N &= \{ x_1, x_4 \}
            \end{aligned}
            $$

    **Iteration 2**
    1. Find the pivot column. As I mentioned from **Iteration 1**, we should find the most negative reduced cost. At this moment, we should select $x_1$ column as a pivot column because it has $-4$ as a cost coefficent.

    2. Next, we select the pivot row to by using minimum ratio test (also mentioned from **Iteration 1**). 

        - $\frac{\frac{2}{3}}{\frac{2}{3}} = 1$
        - $\frac{\frac{4}{3}}{\frac{1}{3}} = 4$
    
    3. Since $1 < 4$, our pivot row will be row 1 (we select the row that has the smallest quotient-- compare quotients with each other after minimum ratio test)

    4. Now, select our new pivot element (the intersection of pivot column and row) and determine our new entering/leaving variables in current iteration to update our basis $B$ (and non basis $N$):

        - Convert our pivot element to 1 to correctly start the pivoting (multiply by $\frac{3}{2}$):
            - $x_1 + \frac{3}{2}x_2 - 2x_4 = 1$
        
        - Rewrite other rows with our new $x_1$ by solving the equation:

            $$
            \begin{aligned} \\
            \frac{1}{3}x_1 + x_2 + \frac{1}{3}x_4 &= \frac{4}{3} \\
            \frac{1}{3}(1 - \frac{3}{2}x_3+2x_4) + x_2 + \frac{1}{3}x_4 &= \frac{4}{3} \\
            \frac{1}{3} - \frac{1}{3}x_3 + \frac{2}{3}x_4 + x_2 + \frac{1}{3}x_4 &= \frac{4}{3} \\
            x_2 - \frac{1}{2}x_3 + x_4 &= 1 \quad \text{(new row 2)}
            \end{aligned}
            $$

        - Rewrite our $z$ with our new $x_1$:

            $$
            \begin{aligned} \\
            z - 4x_1 + 4x_4 &= 16 \\
            z - 4(1 - \frac{3}{2}x_3 + 2x_4) + 4x_4 &= 16 \\
            z - 4 + 6x_3 - 8x_4 + 4x_4 &= 16 \\
            z + 6x_3 - 4x_4 &= 20 \quad \text{(new z)}
            \end{aligned}
            $$
        
        - From now on, $x_1$ is our new **entering variable** (basic variable) and our new **departing variable** (non-basic variable) is $x_3$.

        - Let's update our tableau:

            | **Basis** |  $x_1$  | $x_2$ | $x_3$ |   $x_4$   |  **RHS**  |
            |:---------:|:-------:|:-----:|:-----:|:---------:|:---------:|
            |   $x_1$   |  $1$  |   $0$   |   $\frac{3}{2}$   |  $-2$  |  $1$  |
            |   $x_2$   |  $0$  |   $1$   |   $-\frac{1}{2}$   |  $1$   |  $1$  |
            |    $z$    |    $0$   |   $0$   |   $6$   |     $-4$     |    $20$     |

            $$
            \begin{aligned}
            \text{Basis}: \space B &= \{ x_1, x_2 \} \\
            \text{Non-Basis}: \space N &= \{ x_3, x_4 \}
            \end{aligned}
            $$
    
    **Iteration 3**
    1. We still have a negative cost coefficent (look at $x_4$!), we should run our 3rd iteration. Since $x_4$ has $-4$ as a cost coefficient, our pivot column will be column $x_4$:
    
    2. As usual, use the minimum ratio test to compute each row's quotient:

        - $\frac{1}{-2} = -\frac{1}{2}$
        - $\frac{1}{1} = 1$
    
    3. Since $-\frac{1}{2} < 1$, do we define our row 1 as the pivot row as usual? NO! This is important: We should avoid negative quotients because increasing the entering variable will cause the corresponding basic variable to increase (move away from zero) rather than decrease toward zero. The minimum ratio test seeks the smallest positive quotient to ensure that increasing the entering variable drives some basic variable exactly to zero, maintaining non-negativity. Therefore, our pivot row will be the second row.

    4. Let's select the pivot element and define our new entering/departing variables and update $B$ and $N$:

        - Since our pivot element is already 1, we can directly rewrite our new entering variable $x_4$
            - $x_4 = 1 - x_2 + \frac{1}{2}x_3$

        - Rewrite other rows with our new $x_4$:

            $$
            \begin{aligned} \\
            x_1 + \frac{3}{2}x_2 + 2x_4 &= 1 \\
            x_1 + \frac{3}{2}x_2 + 2(1 - x_2 + \frac{1}{2}x_3) &= 1 \\
            x_1 + \frac{3}{2}x_2 - 2 + 2x_2 - x_3 &= 1 \\
            x_1 + 2x_2 + \frac{1}{2}x_3 &= 3 \quad \text{(new row 1)}
            \end{aligned}
            $$
        
        - Rewrite our $z$ with our new $x_4$:

            $$
            \begin{aligned} \\
            z + 6x_3 - 4x_4 &= 20 \\
            z + 6x_3 - 4(1 - x_2 + \frac{1}{2}x_3) &= 20 \\
            z + 6x_3 - 4 + 4x_2 - 2x_3 &= 20 \\
            z + 4x_2 + 4x_3 &= 24 \quad \text{(new z)}
            \end{aligned}
            $$

        - At this moment, $x_4$ is our new **entering variable** and our new **departing variable** is $x_2$.

        - Now let's update our final version of the tableau:
        
            | **Basis** |  $x_1$  | $x_2$ | $x_3$ |   $x_4$   |  **RHS**  |
            |:---------:|:-------:|:-----:|:-----:|:---------:|:---------:|
            |   $x_1$   |  $1$  |   $2$   |   $\frac{1}{2}$   |  $0$  |  $3$  |
            |   $x_4$   |  $0$  |   $1$   |   $-\frac{1}{2}$   |  $1$   |  $1$  |
            |    $z$    |    $0$   |   $4$   |   $4$   |     $0$     |    $24$     |

            $$
            \begin{aligned}
            \text{Basis}: \space B &= \{ x_1, x_4 \} \\
            \text{Non-Basis}: \space N &= \{ x_2, x_3 \}
            \end{aligned}
            $$

5. Since all cost coefficents are non-negative, the current solution is optimal. The objective function can be written as:

    $$z = 24 - 4x_2 - 4x_3$$

    which achieves its maximum value $z = 24$ when $x_2, x_3 = 0$. At this point, the value of the basic variables are $x_1 = 3$ and $x_4 = 1$.

    The basic variables states that:
    - produce 3 units of $x_1$ (and $0$ units of $x_2$) to get maximized profit of $z = 24$
    - the first constraint is tight (our slack variable $x_3 = 0$), so all of its capacity is fully utilized
    - the second constraint has $1$ unit of slack ($x_4 = 1$), which states it's not fully binding

    Thus, the optimal solution is:

    $$(x_1, x_2, x_3, x_4) = (3, 0, 0, 1)$$

    with objective value:

    $$ z^{*} = 24. \space \blacksquare $$

---
This summary is based on *Linear Programming Notes* [https://math.mit.edu/~goemans/18310S15/lpnotes310.pdf] by Michel Goemans, MIT