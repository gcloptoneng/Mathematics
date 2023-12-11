
Make a plot of $x^4-3 x^2-3=0$. Use the plot to determine the interval [a, b] on which the fixed-point method should be applied to find the root of $f(x) = 0$. Use the fixed-point method to find the root of $f(x) = 0$ to within $10^{-5}$. Use np.roots to check your answer.


```Python
import numpy as np  
import matplotlib.pyplot as plt  
import pandas as pd  
  
x = np.linspace(1, 2, 100)  
f = lambda x: x**4 - 3*x**2 - 3  
  
plt.figure(figsize = (10, 6))  
plt.plot(x, f(x), color ="cyan")  
plt.axhline(0, color = "yellow", linewidth = 0.5)  
plt.axvline(0, color = "yellow", linewidth = 0.5)  
plt.xlim(1, 2)  
plt.ylim(-5, 5)  
plt.grid(color = "grey", linestyle = "--", linewidth = 0.5)  
plt.show()
```


![[Screenshot 2023-12-11 at 01.33.17.png]]



```Python
def fixed_point(p_0, tol = 1e-5, max_iter = 100):

    g = lambda x: (3*x**2 + 3)**(1/4)

    records = []
    for n in range(max_iter):
        p_n = g(p_0)
        records.append([n, p_0, p_n, abs(p_n - p_0)])
        if abs(p_n - p_0) < tol:
            break
        p_0 = p_n

    table = pd.DataFrame(records, columns = ["n", "p_n", "p_n+1", "abs(p_n+1 - p_n)"])
    return table

fixed_point(1.5)

```



|  | $n$ | $p_n$ | $p_n+1$ | $\operatorname{abs}\left(p_{-} n+1-p_{-} n\right)$ |
| :---: | :---: | :---: | :---: | :---: |
| 0 | 0 | 1.500000 | 1.767059 | 0.267059 |
| 1 | 1 | 1.767059 | 1.875299 | 0.108239 |
| 2 | 2 | 1.875299 | 1.918610 | 0.043311 |
| 3 | 3 | 1.918610 | 1.935827 | 0.017217 |
| 4 | 4 | 1.935827 | 1.942651 | 0.006825 |
| 5 | 5 | 1.942651 | 1.945353 | 0.002702 |
| 6 | 6 | 1.945353 | 1.946423 | 0.001069 |
| 7 | 7 | 1.946423 | 1.946846 | 0.000423 |
| 8 | 8 | 1.946846 | 1.947013 | 0.000167 |
| 9 | 9 | 1.947013 | 1.947080 | 0.000066 |

```Python
coefficients = [1, 0, -3, 0, -3]  
np.roots(coefficients)
```


$x_a^3 + 4x_b^2 - 10 = 0$