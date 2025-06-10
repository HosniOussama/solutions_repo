## Linear Algebra

### Problem 1: Calculate the sum **a + c**

Given:  
$$
a = \begin{bmatrix} 2 & 3 \\ 1 & 4 \end{bmatrix}, \quad
c = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}
$$

Add corresponding elements:  
First row: $ 2 + 1 = 3 $, $ 3 + 2 = 5 $  
Second row: $ 1 + 3 = 4 $, $ 4 + 4 = 8 $

**Answer:**  
$$
\begin{bmatrix} 3 & 5 \\ 4 & 8 \end{bmatrix}
$$

---

### Problem 2: Calculate the sum **c + d**

Given:  
$$
c = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}, \quad
d = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}
$$

Add corresponding elements:  
First row: $ 1 + 5 = 6 $, $ 2 + 6 = 8 $  
Second row: $ 3 + 7 = 10 $, $ 4 + 8 = 12 $

**Answer:**  
$$
\begin{bmatrix} 6 & 8 \\ 10 & 12 \end{bmatrix}
$$

---

### Problem 3: Calculate the product **a × d**

Given:  
$$
a = \begin{bmatrix} 2 & 3 \\ 1 & 4 \end{bmatrix}, \quad
d = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}
$$

Multiply row by column:  
First row:  
$ (2 \cdot 5) + (3 \cdot 7) = 10 + 21 = 31 $  
$ (2 \cdot 6) + (3 \cdot 8) = 12 + 24 = 36 $  

Second row:  
$ (1 \cdot 5) + (4 \cdot 7) = 5 + 28 = 33 $  
$ (1 \cdot 6) + (4 \cdot 8) = 6 + 32 = 38 $

**Answer:**  
$$
\begin{bmatrix} 31 & 36 \\ 33 & 38 \end{bmatrix}
$$

---

### Problem 4: Calculate the product **d × c**

Given:  
$$
d = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}, \quad
c = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}
$$

Multiply row by column:  
First row:  
$ 5 \cdot 1 + 6 \cdot 3 = 5 + 18 = 23 $  
$ 5 \cdot 2 + 6 \cdot 4 = 10 + 24 = 34 $  

Second row:  
$ 7 \cdot 1 + 8 \cdot 3 = 7 + 24 = 31 $  
$ 7 \cdot 2 + 8 \cdot 4 = 14 + 32 = 46 $

**Answer:**  
$$
\begin{bmatrix} 23 & 34 \\ 31 & 46 \end{bmatrix}
$$

---

### Problem 5: Determinant of **a**

Given:  
$$
a = \begin{bmatrix} 2 & 3 \\ 1 & 4 \end{bmatrix}
$$

Determinant:  
$$ (2 \cdot 4) - (3 \cdot 1) = 8 - 3 = 5 $$

**Answer:**  
$$
5
$$

---

### Problem 6: Determinant of **c**

Given:  
$$
c = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}
$$

Determinant:  
$$ 1 \cdot 4 - 2 \cdot 3 = 4 - 6 = -2 $$

**Answer:**  
$$
-2
$$

---

### Problem 7: Determinant of **d**

Given:  
$$
d = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}
$$

Determinant:  
$$ 5 \cdot 8 - 6 \cdot 7 = 40 - 42 = -2 $$

**Answer:**  
$$
-2
$$

---

### Problem 8: Inverse of **a**

Given:  
$$
a = \begin{bmatrix} 2 & 3 \\ 1 & 4 \end{bmatrix}
$$

Determinant = 5. Inverse:  
$$
\frac{1}{5} \begin{bmatrix} 4 & -3 \\ -1 & 2 \end{bmatrix}
= \begin{bmatrix} 0.8 & -0.6 \\ -0.2 & 0.4 \end{bmatrix}
$$

**Answer:**  
$$
\begin{bmatrix} 0.8 & -0.6 \\ -0.2 & 0.4 \end{bmatrix}
$$

---

### Problem 9: Inverse of **c**

Given:  
$$
c = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}
$$

Determinant = -2. Inverse:  
$$
\frac{1}{-2} \begin{bmatrix} 4 & -2 \\ -3 & 1 \end{bmatrix}
= \begin{bmatrix} -2 & 1 \\ 1.5 & -0.5 \end{bmatrix}
$$

**Answer:**  
$$
\begin{bmatrix} -2 & 1 \\ 1.5 & -0.5 \end{bmatrix}
$$

---

### Problem 10: Solve the system using matrix method

Given:  
$$
\begin{cases}
x + 2y = 8 \\
3x + 4y = 18
\end{cases}
$$

Let  
$$
A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}, \quad
\mathbf{b} = \begin{bmatrix} 8 \\ 18 \end{bmatrix}
$$

Using inverse from Problem 9:  
$$
A^{-1} = \begin{bmatrix} -2 & 1 \\ 1.5 & -0.5 \end{bmatrix}
$$

Then:  
$$
\mathbf{x} = A^{-1} \cdot \mathbf{b} =
\begin{bmatrix} 2 \\ 3 \end{bmatrix}
$$

**Answer:** $ x = 2, y = 3 $

---

### Problem 11: Solve using elimination

Given:  
$$
\begin{cases}
x + 2y = 8 \\
3x + 4y = 18
\end{cases}
$$

Multiply first equation by 3:  
$3x + 6y = 24$

Subtract second:  
$2y = 6 \Rightarrow y = 3$

Substitute back:  
$x + 6 = 8 \Rightarrow x = 2$

**Answer:** $ x = 2, \ y = 3 $

---

### Problem 12: Why is the solution unique?

Given:  
$$
A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}
$$

Determinant = $ 4 - 6 = -2 \neq 0 $  
So the solution is **unique**.

---

### Problem 13: Solve using matrix method

Given:  
$$
\begin{cases}
2x - y = 1 \\
x + y = 4
\end{cases}
$$

Let  
$$
A = \begin{bmatrix} 2 & -1 \\ 1 & 1 \end{bmatrix}, \quad
\mathbf{b} = \begin{bmatrix} 1 \\ 4 \end{bmatrix}
$$

Determinant:  
$ 2 \cdot 1 - (-1 \cdot 1) = 3 $

Inverse:  
$$
\frac{1}{3} \begin{bmatrix} 1 & 1 \\ -1 & 2 \end{bmatrix}
= \begin{bmatrix} 0.333 & 0.333 \\ -0.333 & 0.667 \end{bmatrix}
$$

Then:  
$$
x \approx 1.67, \quad y \approx 2.33
$$

---

### Problem 14: Solve using elimination

Add equations:  
$ (2x - y) + (x + y) = 3x = 5 \Rightarrow x = \frac{5}{3} \approx 1.67 $

Substitute back:  
$x + y = 4 \Rightarrow y = \frac{7}{3} \approx 2.33$

**Answer:** $ x \approx 1.67, \ y \approx 2.33 $

---

### Problem 15: Length of vector $ \vec{v} = (2, -1) $

Length:  
$$
|\vec{v}| = \sqrt{2^2 + (-1)^2} = \sqrt{5} \approx 2.24
$$

---

### Problem 16: Dot product of \( \vec{v} = (2, -1) \), \( \vec{w} = (3, 4) \)

Dot product:  
$$
\vec{v} \cdot \vec{w} = 2 \cdot 3 + (-1) \cdot 4 = 6 - 4 = 2
$$

---

### Problem 17: Angle between $ \vec{v} $ and $ \vec{w} $

$$
\cos\theta = \frac{\vec{v} \cdot \vec{w}}{|\vec{v}| \cdot |\vec{w}|}
= \frac{2}{\sqrt{5} \cdot 5} \approx 0.179
\Rightarrow \theta \approx \cos^{-1}(0.179) \approx 79.7^\circ
$$

**Answer:** $ \theta \approx 79.7^\circ $
