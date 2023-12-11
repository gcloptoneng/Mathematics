
# 19.1 Numerical Solution of Non-Linear Equations in a Single Unknown

## Fixed-Point Iteration


##### Problem

Given $x^2-x-6=0$, find the first approximation of the solution $x^*$ for the given equation by transforming it into the form $f_1(x)=f_2(x)$ and plotting the functions.

###### Solution

We will find the first approximation of the solution $x^*$ for the given equation $x^2-x-6=$ 0 by transforming it into the form $f_1(x)=f_2(x)$ and plotting the functions.
First, we need to rewrite the given equation $x^2-x-6=0$ in a form suitable for iteration. We can do this in multiple ways, such as $x=\sqrt{x+6}$ or $x=\frac{x^2-6}{x}$. Let's choose the first one for simplicity: $x=\sqrt{x+6}$. So we have:

- Let $f_1(x)=x$.
- Let $f_2(x)=\sqrt{x+6}$.

We will plot both $f_1(x)$ and $f_2(x)$ on the same graph. The intersection point(s) of these graphs will give us the approximate solution(s) to the original equation. The $x$-coordinate(s) of the point(s) where the two graphs intersect is the approximate solution $x^*$.

```Python
import matplotlib.pyplot as plt
import numpy as np

# Define the range for x values
x = np.linspace(-6, 5, 400) # start from -6 to avoid negative values under the square root

# Define f1(x) and f2(x)
f1 = x
f2 = np.sqrt(x + 6)

# Create the plot
plt.figure(figsize=(8, 6))
plt.plot(x, f1, label="f1(x) = x")
plt.plot(x, f2, label="f2(x) = sqrt(x + 6)")

# Adjust the x-axis and y-axis limits and ticks
plt.xlim(-6, 5)
plt.ylim(-6, 5)
plt.xticks(np.arange(-6, 6, 1)) # x-axis tic marks in increments of 1
plt.yticks(np.arange(-6, 6, 1)) # y-axis tic marks in increments of 1 for consistency

# Other plot settings
plt.axhline(0, color='black', linewidth=0.5)
plt.axvline(0, color='black', linewidth=0.5)
plt.grid(color='gray', linestyle='--', linewidth=0.5)
plt.title("Graphs of f1(x) and f2(x) with x-axis Tic Marks in Increments of 1")
plt.xlabel("x")
plt.ylabel("f(x)")
plt.legend()
plt.show()
```


![[Pasted image 20231128035959.png|500]]


##### Problem

Given $f(x) = x^2 - sin(x)$ , find the first approximation of the solution $x^*$ for the given equation by transforming it into the form $f_1(x)=f_2(x)$ and plotting the functions. **The size of the plot should be 8 by 6.**

![[Pasted image 20231128040637.png|500]]

##### Solution

To estimate the roots for the equation $f(x)=x^2-\sin x=0$ using a graphical approach, we can follow a similar procedure as before. The key is to transform the equation into the form $f_1(x)=f_2(x)$ and then plot these functions to find their intersection points. The $x$-coordinates of these intersection points will provide an approximation of the roots of the original equation.
1. Transform the Equation: Rewrite the equation as $x^2=\sin x$. This gives us two functions:
- Let $f_1(x)=x^2$.
- Let $f_2(x)=\sin x$.
2. Plot the Functions: Plot $f_1(x)$ and $f_2(x)$ on the same graph.
3. Find Intersection Points: The $x$-coordinates of the intersection points of these graphs will be the approximate solutions to $x^2-\sin x=0$.

###### Sketch

![[Screenshot 2023-12-03 at 01.29.00.png]]
###### Code

```Python
import numpy as np
import matplotlib.pyplot as plt

# Define the range for x values
x = np.linspace(-2, 2, 400)

# Define f1(x) and f2(x)
f1 = x**2
f2 = np.sin(x)

# Create the plot
plt.figure(figsize=(8, 6))
plt.plot(x, f1, color='red', label="f1(x) = x^2")
plt.plot(x, f2, color='blue', label="f2(x) = sin(x)")

# Adjust the x-axis and y-axis limits and ticks
plt.xlim(-2, 2)
plt.ylim(-1, 4)
plt.xticks(np.arange(-2, 3, 1))
plt.yticks(np.arange(-1, 5, 1))

# Other plot settings
plt.axhline(0, color='black', linestyle='--', linewidth=0.5)
plt.axvline(0, color='black', linestyle='--', linewidth=0.5)
plt.grid(color='gray', linestyle='--', linewidth=0.5)
plt.title("Graphs of f1(x) and f2(x)")
plt.xlabel("x")
plt.ylabel("f(x)")
plt.legend()
plt.show()

```


![[Pasted image 20231128040637.png|500]]

The graph displays the functions $f_1(x)=x^2$ and $f_2(x)=\sin (x)$. The intersection points of these graphs approximate the solutions to the equation $x^2-\sin x=0$.

$f(x)=x^2-\sin x=0$. From the shapes of the curves $y=x^2$ and $y=\sin x$ it can be seen that $x_1^*=0$ and $x_2^* \approx 0.87$ are roots (Fig. 19.1)



##### Problem

**Implement the fixed-point iteration method to solve the equation $x^2=\sin (x)$. Begin with an initial guess of $x_0=0.87$ and employ a tolerance level of $10^{-6}$ for the stopping criterion. Continue the iterations until the absolute change in $x$ is less than this tolerance or when 100 iterations have been completed, whichever occurs first.**
**During each iteration, record:**
**1. Iteration number $(n)$**
**2. Current approximation $\left(x_n\right)$**
**3. Absolute change from the previous approximation**
**Develop a Python function named 'results_table " that executes this fixed-point iteration process. The function should return a pandas DataFrame with the iteration details. Each row of the DataFrame must correspond to an iteration and include values up to 10 decimal places.**

###### Sketch

![[Sketch Fixed Point Iteration 1.png]]


###### Code

```Python
import pandas as pd
import sympy as sp

# Constants
tolerance = 1e-6
x_0 = 0.87
max_iter = 100

# Define the symbol
x = sp.symbols('x')

# Define the function
phi = sp.sqrt(sp.sin(x))

# Fixed point iteration function
def fixed_point_iteration_table_with_change(tolerance, x_0, max_iter):
    records = []
    x_n = x_0

    for n in range(max_iter):
        x_next = phi.subs(x, x_n)
        if n > 0:
            change = abs(x_next - x_n)
            records.append([n, x_n, sp.sin(x_n), change])
            if change < tolerance:
                break
            x_n = x_next

    # Convert to DataFrame
    df = pd.DataFrame(records, columns=['n', 'x_n', 'sin(x_n)', 'change'])
    return df

# Perform iteration
results_table_with_change = fixed_point_iteration_table_with_change(tolerance, x_0, max_iter)

# Display results
print(results_table_with_change)
```


# Newton's Method

Employ Newton's method to approximate the square root of 2. Begin with an initial guess of $x_0=1.5$. Perform the iteration four times to approximate $\sqrt{2}$. Provide each step of your iteration and the resulting approximation of $\sqrt{2}$ after the fourth iteration. How does the approximation compare to the actual value of $\sqrt{2}$ ?


```Python
import numpy as np
import matplotlib.pyplot as plt

f = x**2 - 2

plt.plot(x, f, label = "x")
plt.xlim(1.2, 1.5)
plt.ylim(-0.5, 1.5)
plt.xticks(np.arange(1.2, 1.6, 0.1))
plt.axhline(0, color="red", linewidth=0.5)
plt.axvline(0, color="red", linewidth=0.5)
plt.grid(color="grey", linestyle="--", linewidth=0.5)
```


![[Pasted image 20231203021749.png]]

From this plot, we can see that 1.4 is a good initial guess, so we'll set x_n = 1.4

```Python
import pandas as pd
import sympy as sp

# Constants
tol = 1e-15
x_0 = 1.5
max_iter = 100
a = 2

# Define the symbol
x = sp.symbols('x')

# Function definitions as symbolic expressions
f = x**2 - a
d_f = sp.diff(f, x)  # Differentiate once, use many times

# Newton's Method
def newtons_method(tol, x_0, max_iter):
    records = []
    x_n = x_0

    for n in range(max_iter):
        f_val = f.subs(x, x_n).evalf()  # Evaluate f at x_n
        df_val = d_f.subs(x, x_n).evalf()  # Evaluate derivative at x_n
        x_next = x_n - f_val / df_val
        change = abs(x_next - x_n)

        records.append([n, x_next, x_n, change])

        if change < tol:
            break
        x_n = x_next

    pd.set_option('display.precision', 10)
    df = pd.DataFrame(records, columns=['n', 'x_next', 'x_n', 'change'])
    return df

result = newtons_method(tol, x_0, max_iter)
print(result)
```



# Regula Falsi



```Python
import numpy as np
import pandas as pd

# Define the function f(x)
def f(x):
    return x**2 - np.sin(x)

# Define initial guesses
x0 = 0.9
x1 = 0.87

# Regula falsi method without using a data dictionary
def regula_falsi_df(f, x0, x1, tol=1e-5, max_iter=100):
    rows = []

    # Add initial values manually
    rows.append([0, None, x0, f(x0), None, None])
    rows.append([1, None, x1, f(x1), None, None])

    for i in range(2, max_iter + 2):
        x2 = x1 - f(x1) * (x1 - x0) / (f(x1) - f(x0))
        
        Δx_n = x2 - x1
        Δy_n = f(x2) - f(x1)
        
        # Add the iteration data to the rows list
        rows.append([i, Δx_n, x2, f(x2), Δy_n, Δx_n / Δy_n if Δy_n != 0 else None])
        
        # Check for convergence
        if np.abs(f(x2)) < tol or np.abs(Δx_n) < tol:
            break
        
        if f(x0) * f(x2) < 0:
            x1 = x2
        else:
            x0 = x2

    # Create the dataframe from rows
    df = pd.DataFrame(rows, columns=['n', 'Δx_n', 'x_n', 'f(x_n)', 'Δy_n', 'Δx_n/Δy_n'])
    
    return x2, i - 2, df

# Call the regula falsi method to get the dataframe
root, iterations, df_no_data = regula_falsi_df(f, x0, x1)

# Display the dataframe
df_no_data.fillna('')  # Replace NaN with empty string to match the image presentation
```