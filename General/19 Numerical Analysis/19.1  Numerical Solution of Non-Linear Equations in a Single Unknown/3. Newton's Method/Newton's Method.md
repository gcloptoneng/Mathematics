


```Python
import sympy as sp
import pandas as pd

# Define the symbol
x = sp.symbols('x')

# Define the function using sympy
f_sympy = sp.cos(x) - x

# Compute the derivative of the function
df_sympy = sp.diff(f_sympy, x)

# Convert the sympy expressions to functions that can be evaluated
f_lambdified = sp.lambdify(x, f_sympy, 'numpy')
df_lambdified = sp.lambdify(x, df_sympy, 'numpy')

# Redefine Newton's method to use the lambdified functions
def newtons_method_sympy(p_0, tol, max_iter):
    # Initialize variables
    p = p_0
    iteration_data = []
    
    # Iterate according to Newton's method
    for n in range(1, max_iter + 1):
        p_n = p - f_lambdified(p) / df_lambdified(p)  # Compute the next approximation
        iteration_data.append([n, p_n, abs(p_n - p)])  # Append iteration data
        
        if abs(p_n - p) < tol:  # If the result is within the desired tolerance
            break
        
        p = p_n  # Update p for the next iteration
    
    # Create a DataFrame with the results
    df_results = pd.DataFrame(iteration_data, columns=['n', 'p_n', 'abs(p - p_0)'])
    return df_results

p_0 = 0.5  # Initial approximation
tol = 1e-5  # Tolerance
max_iter = 10  # Maximum number of iterations

# Run Newton's method with the automatically derived derivative
results_sympy = newtons_method_sympy(p_0, tol, max_iter)
results_sympy
```


![[Screenshot 2023-12-11 at 08.38.06.png]]