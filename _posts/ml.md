Let's delve into the third step of polynomial regression, where we calculate the **normal equations**. This step is crucial because it allows us to find the coefficients \( b_0, b_1, b_2, \dots, b_n \) that best fit our polynomial model to the data.

### Step 3: Calculate the Normal Equations

#### The Goal:
The normal equations are derived from the method of **least squares**, which minimizes the sum of squared differences between the observed values and the values predicted by our model. The goal is to find the coefficients \( \mathbf{b} = [b_0, b_1, b_2, \dots, b_n] \) that minimize this error.

#### The Design Matrix \( \mathbf{X} \):
For a polynomial regression of degree \( n \), the design matrix \( \mathbf{X} \) contains columns for each power of the predictor variable \( X \), starting from \( X^0 = 1 \) (which accounts for the intercept) up to \( X^n \).

For example, for a quadratic regression (where \( n = 2 \)), the design matrix \( \mathbf{X} \) looks like this for three data points:

\[
\mathbf{X} = \begin{bmatrix}
1 & X_1 & X_1^2 \\
1 & X_2 & X_2^2 \\
1 & X_3 & X_3^2
\end{bmatrix}
\]

#### The Normal Equation:
The normal equation to solve for the coefficient vector \( \mathbf{b} \) is:

\[
\mathbf{X}^T \mathbf{X} \mathbf{b} = \mathbf{X}^T \mathbf{y}
\]

Where:
- \( \mathbf{X}^T \) is the transpose of the design matrix \( \mathbf{X} \).
- \( \mathbf{X}^T \mathbf{X} \) is the matrix product of \( \mathbf{X}^T \) and \( \mathbf{X} \).
- \( \mathbf{X}^T \mathbf{y} \) is the matrix product of \( \mathbf{X}^T \) and the vector of observed values \( \mathbf{y} \).
- \( \mathbf{b} = [b_0, b_1, b_2] \) is the vector of coefficients.

#### Why This Works:
The normal equation is a result of setting the partial derivatives of the cost function (the sum of squared errors) with respect to each coefficient \( b_0, b_1, \dots, b_n \) equal to zero. Solving this system of equations gives us the coefficients that minimize the cost function.

### Example Walkthrough:

Let's continue with the quadratic example using the dataset:

- \( (X_1, y_1) = (1, 2) \)
- \( (X_2, y_2) = (2, 4) \)
- \( (X_3, y_3) = (3, 7) \)

1. **Design Matrix \( \mathbf{X} \):**

   \[
   \mathbf{X} = \begin{bmatrix}
   1 & 1 & 1^2 \\
   1 & 2 & 2^2 \\
   1 & 3 & 3^2
   \end{bmatrix} = \begin{bmatrix}
   1 & 1 & 1 \\
   1 & 2 & 4 \\
   1 & 3 & 9
   \end{bmatrix}
   \]

2. **Transpose of \( \mathbf{X} \):**

   The transpose \( \mathbf{X}^T \) is:

   \[
   \mathbf{X}^T = \begin{bmatrix}
   1 & 1 & 1 \\
   1 & 2 & 3 \\
   1 & 4 & 9
   \end{bmatrix}
   \]

3. **Calculate \( \mathbf{X}^T \mathbf{X} \):**

   Multiply \( \mathbf{X}^T \) by \( \mathbf{X} \):

   \[
   \mathbf{X}^T \mathbf{X} = \begin{bmatrix}
   1 & 1 & 1 \\
   1 & 2 & 3 \\
   1 & 4 & 9
   \end{bmatrix} \begin{bmatrix}
   1 & 1 & 1 \\
   1 & 2 & 4 \\
   1 & 3 & 9
   \end{bmatrix} = \begin{bmatrix}
   3 & 6 & 14 \\
   6 & 14 & 36 \\
   14 & 36 & 98
   \end{bmatrix}
   \]

   This gives us a symmetric matrix where each element represents the sum of products of the respective powers of \( X \) values.

4. **Calculate \( \mathbf{X}^T \mathbf{y} \):**

   Multiply \( \mathbf{X}^T \) by \( \mathbf{y} \) (where \( \mathbf{y} = [y_1, y_2, y_3]^T = [2, 4, 7]^T \)):

   \[
   \mathbf{X}^T \mathbf{y} = \begin{bmatrix}
   1 & 1 & 1 \\
   1 & 2 & 3 \\
   1 & 4 & 9
   \end{bmatrix} \begin{bmatrix}
   2 \\
   4 \\
   7
   \end{bmatrix} = \begin{bmatrix}
   13 \\
   29 \\
   71
   \end{bmatrix}
   \]

   This vector contains the sums of the products of the observed \( y \) values and the corresponding powers of \( X \).

5. **Solve for \( \mathbf{b} \):**

   Now, you solve the equation:

   \[
   \mathbf{X}^T \mathbf{X} \mathbf{b} = \mathbf{X}^T \mathbf{y}
   \]

   In matrix terms:

   \[
   \begin{bmatrix}
   3 & 6 & 14 \\
   6 & 14 & 36 \\
   14 & 36 & 98
   \end{bmatrix} \begin{bmatrix}
   b_0 \\
   b_1 \\
   b_2
   \end{bmatrix} = \begin{bmatrix}
   13 \\
   29 \\
   71
   \end{bmatrix}
   \]

   To solve for \( \mathbf{b} \), you would typically use matrix inversion (or other numerical methods like Gaussian elimination). The solution \( \mathbf{b} = [b_0, b_1, b_2] \) gives the coefficients of the polynomial.

### Conclusion:

The normal equations step is where you set up and solve a system of linear equations to find the best-fitting polynomial coefficients. This step generalizes to higher-degree polynomials and more complex models but follows the same fundamental principles of linear algebra and least squares optimization.