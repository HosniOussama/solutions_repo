#  Linear algebra
### Problem 1: Calculate the sum $a + c$

Given: $$ a = \begin{bmatrix} 2 & 3 \ 1 & 4 \end{bmatrix}, c = \begin{bmatrix} 1 & 2 \ 3 & 4 \end{bmatrix} $$
Solution: Add corresponding elements:

First row: $ 2 + 1 = 3 $, $ 3 + 2 = 5 $

Second row: $ 1 + 3 = 4 $, $ 4 + 4 = 8 $


Answer: $$ \begin{bmatrix} 3 & 5 \ 4 & 8 \end{bmatrix} $$

### Problem 2: Calculate the sum $c + d$

Given: $$ c = \begin{bmatrix} 1 & 2 \ 3 & 4 \end{bmatrix}, d = \begin{bmatrix} 5 & 6 \ 7 & 8 \end{bmatrix} $$
Solution: Add corresponding elements:

First row: $ 1 + 5 = 6 $, $ 2 + 6 = 8 $

Second row: $ 3 + 7 = 10 $, $ 4 + 8 = 12 $


Answer: $$ \begin{bmatrix} 6 & 8 \ 10 & 12 \end{bmatrix} $$

Problem 3: Calculate the product $a * d$

Given: $$ a = \begin{bmatrix} 2 & 3 \ 1 & 4 \end{bmatrix}, d = \begin{bmatrix} 5 & 6 \ 7 & 8 \end{bmatrix} $$

Solution: Multiply row by column:

First row: $ (2 \cdot 5) + (3 \cdot 7) = 10 + 21 = 31 $, $ (2 \cdot 6) + (3 \cdot 8) = 12 + 24 = 36 $

Second row: $ (1 \cdot 5) + (4 \cdot 7) = 5 + 28 = 33 $, $ (1 \cdot 6) + (4 \cdot 8) = 6 + 32 = 38 $


Answer: $$ \begin{bmatrix} 31 & 36 \ 33 & 38 \end{bmatrix} $$

### Problem 4: Calculate the product $ d * c $

Given: $$ d = \begin{bmatrix} 5 & 6 \ 7 & 8 \end{bmatrix}, c = \begin{bmatrix} 1 & 2 \ 3 & 4 \end{bmatrix} $$
Solution: Multiply row by column:
First row: $ (5 \cdot 1) + (6 \cdot 3) = 5 + 18 = 23 $, $ (5 \cdot 2) + (6 \cdot 4) = 10 + 24 = 34 $
Second row: $ (7 \cdot 1) + (8 \cdot 3) = 7 + 24 = 31 $, $ (7 \cdot 2) + (8 \cdot 4) = 14 + 32 = 46 $


Answer: $$ \begin{bmatrix} 23 & 34 \ 31 & 46 \end{bmatrix} $$

### Problem 5: Calculate the determinant of a

Given: $$ a = \begin{bmatrix} 2 & 3 \ 1 & 4 \end{bmatrix} $$
Solution: Determinant = $ (2 \cdot 4) - (3 \cdot 1) = 8 - 3 = 5 $

Answer: $$ 5 $$

Problem 6: Calculate the determinant of c

Given: $$ c = \begin{bmatrix} 1 & 2 \ 3 & 4 \end{bmatrix} $$
Solution: Determinant = $ (1 \cdot 4) - (2 \cdot 3) = 4 - 6 = -2 $

Answer: $$ -2 $$

### Problem 7: Calculate the determinant of d

Given: $$ d = \begin{bmatrix} 5 & 6 \ 7 & 8 \end{bmatrix} $$
Solution: Determinant = $ (5 \cdot 8) - (6 \cdot 7) = 40 - 42 = -2 $

Answer: $$ -2 $$

### Problem 8: Calculate the inverse of a (if it exists)

Given: $$ a = \begin{bmatrix} 2 & 3 \ 1 & 4 \end{bmatrix} $$
Solution: Determinant = 5. Inverse = $ \frac{1}{5} \begin{bmatrix} 4 & -3 \ -1 & 2 \end{bmatrix} $

$ \frac{1}{5} \cdot 4 = 0.8 $, $ \frac{1}{5} \cdot (-3) = -0.6 $

$ \frac{1}{5} \cdot (-1) = -0.2 $, $ \frac{1}{5} \cdot 2 = 0.4 $


Answer: $$ \begin{bmatrix} 0.8 & -0.6 \ -0.2 & 0.4 \end{bmatrix} $$

### Problem 9: Calculate the inverse of $c$ (if it exists)

Given: $$ c = \begin{bmatrix} 1 & 2 \ 3 & 4 \end{bmatrix} $$
Solution: Determinant = -2. Inverse = $$ \frac{1}{-2} \begin{bmatrix} 4 & -2 \ -3 & 1 \end{bmatrix} $$
$ \frac{1}{-2} \cdot 4 = -2 $, $ \frac{1}{-2} \cdot (-2) = 1 $
$ \frac{1}{-2} \cdot (-3) = 1.5 $, $ \frac{1}{-2} \cdot 1 = -0.5 $


Answer: $$ \begin{bmatrix} -2 & 1 \ 1.5 & -0.5 \end{bmatrix} $$

### Problem 10: Solve the system of equations using the matrix method

Given:$$ \begin{cases} x + 2y = 8 \ 3x + 4y = 18 \end{cases} $$
Solution: $ A = \begin{bmatrix} 1 & 2 \ 3 & 4 \end{bmatrix}, \mathbf{b} = \begin{bmatrix} 8 \ 18 \end{bmatrix} $
Inverse of $ A $ (from Problem 9): $$ \begin{bmatrix} -2 & 1 \ 1.5 & -0.5 \end{bmatrix} $$
$ \mathbf{x} = A^{-1} \cdot \mathbf{b} $:

$ x = (-2 \cdot 8) + (1 \cdot 18) = -16 + 18 = 2 $

$ y = (1.5 \cdot 8) + (-0.5 \cdot 18) = 12 - 9 = 3 $




Answer: $x = 2, y = 3$

### Problem 11: Solve the system of equations using the elimination method

Given:$$ \begin{cases} x + 2y = 8 \ 3x + 4y = 18 \end{cases} $$
Solution: Eliminate $ x $:

Multiply first equation by $3$:  $ 3x + 6y = 24 $

Subtract second equation: $ (3x + 6y) - (3x + 4y) = 24 - 18 $
$ 2y = 6 $, so $ y = 3 $

Substitute $ y = 3 $ into $ x + 2y = 8 $: $ x + 6 = 8 $, so $ x = 2 $


Answer: $x = 2, y = 3$

### Problem 12: Why is the solution of the system unique by using the determinant?

Given:$$ A = \begin{bmatrix} 1 & 2 \ 3 & 4 \end{bmatrix} $$

Solution: A system has a unique solution if the determinant is non-zero.

Determinant = $ (1 \cdot 4) - (2 \cdot 3) = 4 - 6 = -2 $, which is non $-$ zero.

Answer: The solution is unique because the determinant of the coefficient matrix is $-2$, not zero.

### Problem 13: Solve the system of equations using the matrix method

Given:$$ \begin{cases} 2x - y = 1 \ x + y = 4 \end{cases} $$

Solution: $ A = \begin{bmatrix} 2 & -1 \ 1 & 1 \end
{bmatrix}, \mathbf{b} = \begin{bmatrix} 1 \ 4 \end{bmatrix} $

Determinant = $ (2 \cdot 1) - (-1 \cdot 1) = 2 + 1 = 3 $

Inverse = $ \frac{1}{3} \begin{bmatrix} 1 & 1 \ -1 & 2 \end{bmatrix} = \begin{bmatrix} 0.333 & 0.333 \ -0.333 & 0.667 \end{bmatrix} $

$ \mathbf{x} = A^{-1} \cdot \mathbf{b} $:
$ x = (0.333 \cdot 1) + (0.333 \cdot 4) = 0.333 + 1.332 = 1.665 $

$ y = (-0.333 \cdot 1) + (0.667 \cdot 4) = -0.333 + 2.668 = 2.335 $




Answer: $x ≈ 1.67, y ≈ 2.33$

Problem 14: Solve the system of equations using the elimination method

Given:$$ \begin{cases} 2x - y = 1 \ x + y = 4 \end{cases} $$

Solution: Add the equations to eliminate $ y $:
$ (2x - y) + (x + y) = 1 + 4 $
$ 3x = 5 $, so $ x = \frac{5}{3} \approx 1.67 $

Substitute $ x = \frac{5}{3} $ into $ x + y = 4 $: $ \frac{5}{3} + y = 4 $, $ y = 4 - \frac{5}{3} = \frac{12}{3} - \frac{5}{3} = \frac{7}{3} \approx 2.33 $


Answer: $x ≈ 1.67,   y ≈ 2.33$


Problem 15: Calculate the length of the vector $v = (2, -1)$

Solution: Length = $ \sqrt{2^2 + (-1)^2} = \sqrt{4 + 1} = \sqrt{5} \approx 2.24 $
Answer: $(\sqrt{5} \approx 2.24)$

Problem 16: Find the dot product of vectors $v = (2, -1)$ and $w = (3, 4)$

Solution: Dot product = $ (2 \cdot 3) + (-1 \cdot 4) = 6 - 4 = 2 $
Answer: 2

Problem 17: Find the angle between vectors $v = (2, -1)$ and $w = (3, 4)$

Solution: Use $ \cos\theta = \frac{v \cdot w}{|v| |w|} $
$ |v| = \sqrt{5} $, $ |w| = \sqrt{3^2 + 4^2} = \sqrt{9 + 16} = \sqrt{25} = 5 $

$ \cos\theta = \frac{2}{\sqrt{5} \cdot 5} = \frac{2}{5\sqrt{5}} \approx 0.179 $

$ \theta = \cos^{-1}(0.179) \approx 79.7^\circ $


Answer: $(\approx 79.7^\circ)$
