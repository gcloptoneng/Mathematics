

1. Make plot for $f(x) = x^3 + 4x^2 - 10$, and use it to find the range in which the solution lies. Then use the bisection method to estimate the solution to a tolerance of $1 \times 10^{-5}$


```Python
import numpy as np
import matplotlib.pyplot as plt

# Define the range for x values
x = np.linspace(-2, 2, 400)

# define f
f = x**3 + 4*x**2 - 10

#create plot
plt.figure(figsize = (8, 6))
plt.plot(x, f, color = 'blue', label = "f(x) = x^3 + 4x^2 - 10")
plt.axhline(0, color = "red", linestyle = '--', linewidth = 0.5)
plt.axvline(0, color = "red", linestyle = '--', linewidth = 0.5)


plt.grid(color = "gray")
plt.title("Plot of f(x) = x^3 + 4x^2 - 10")
plt.xlabel("x")
plt.ylabel("f(x)")
plt.legend()
plt.show()
```

![[Bisection Method 1.png]]

3. Determine the interval [a, b] over which you need to make your plot. in this case it is xlim(-1, 2), ylim(-1, 1)

```Python
import numpy as np
import matplotlib.pyplot as plt

# Define the range for x values
x = np.linspace(-2, 2, 400)

# define f
f = x**3 + 4*x**2 - 10

#create plot
plt.figure(figsize = (8, 6))
plt.plot(x, f, color = 'blue', label = "f(x) = x^3 + 4x^2 - 10")
plt.axhline(0, color = "red", linestyle = '--', linewidth = 0.5)
plt.axvline(0, color = "red", linestyle = '--', linewidth = 0.5)
plt.xlim(1, 2)
plt.ylim(-1, 1)

plt.grid(color = "gray")
plt.title("Plot of f(x) = x^3 + 4x^2 - 10")
plt.xlabel("x")
plt.ylabel("f(x)")
plt.legend()
plt.show()
```


```Python

import pandas as pd
import math

# Corrected function definition
def f(x):
    return x**3 + 4*x**2 - 10  # Use math.sqrt for single numbers

# Updated Bisection method
def bisection_updated(a, b, tol, max_iter):
    if f(a) * f(b) >= 0:
        print("Bisection method fails.")
        return None
    a_n = a
    b_n = b
    iter_data = []  # List to store iteration data
    for n in range(1, max_iter + 1):
        m_n = (a_n + b_n) / 2
        f_m_n = f(m_n)
        iter_data.append([n, a_n, b_n, m_n, f_m_n])  # Append iteration data
        if abs(f_m_n) < tol:
            break
        elif f(a_n) * f_m_n < 0:
            b_n = m_n
        else:
            a_n = m_n
    table = pd.DataFrame(iter_data, columns=['n', 'a_n', 'b_n', 'p_n', 'f(p_n)'])  # Create DataFrame once
    return m_n, table

# Adjust max_iter for desired iterations
root_updated, table_updated = bisection_updated(1, 2, 1e-5, 13)
table_updated


```



