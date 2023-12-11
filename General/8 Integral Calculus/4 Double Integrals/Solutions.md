
**Calculate the integral $A=\int_S x y^2 d S$ over the region $S$ bounded by the parabola $y=x^2$ and the line $y=2 x$.**

We need to find the intersection points of $y=x^2$ and $y=2 x$ to determine the limits of integration for $x$. The parabola and the line intersect where $x^2=2 x$. This equation can be solved by setting $x^2-2 x=0$, factoring out $x$ to get $x(x-2)=0$. This gives us two points, $x=0$ and $x=2$, which are the bounds for $x$ in the double integral.

We can also find the intersection using python:

```Python
from sympy import symbols, Eq, solve, integrate

#Define the symbols
x, y = symbols('x, y')

#Define the equations
eq1 = Eq(y, x**2)
eq2 = Eq(y, 2*x)

#Solve for the intersection points
intersection_points = solve((eq1, eq2), (x, y))
intersection_points
```


Now, set up the integral for $A$. For a given $x$ in the interval [0, 2], $y$ ranges from $x^2$ to $2 x$. So, the integral becomes:
$$
A=\int_0^2 \int_{x^2}^{2 x} x y^2 d y d x
$$

Now we'll calculate the integral. I'll show you how to do a step-wise evaluation as well as a one-step evaluation

## Step-Wise Evaluation

```Python
# First, perform the inner integration with respect to y
inner_integral = integrate(x * y**2, (y, x**2, 2*x))

# Now, perform the outer integration with respect to x
outer_integral = integrate(inner_integral, (x, 0, 2))

inner_integral, outer_integral
```


## One-Step Evaluation

```Python
# Define the limits for x and y
x_lower = 0
x_upper = 2
y_lower = x**2
y_upper = 2*x

# Define the function to integrate
f = x * y**2

# Set up the double integral
integral_A = integrate(integrate(f, (y, y_lower, y_upper)), (x, x_lower, x_upper))
integral_A
```




The integral $A=\int_S x y^2 d S$, where $S$ is the surface region between the parabola $y=x^2$ and the line $y=2 x$, is equal to $\frac{32}{5}$.

For the plot, we have:

```Python
import matplotlib.pyplot as plt
import numpy as np

# Define the functions
def parabola(x):
    return x**2

def line(x):
    return 2*x

# Define the range for x values
x_values = np.linspace(0, 2, 400)

# Plot the area between the parabola and line
plt.fill_between(x_values, parabola(x_values), line(x_values), color='gray', alpha=0.5, label='Region S')

# Plot the parabola y = x^2
plt.plot(x_values, parabola(x_values), label='$y = x^2$')

# Plot the line y = 2x
plt.plot(x_values, line(x_values), label='$y = 2x$')

# Set the limit for the y-axis
plt.ylim(0, 4)

# Add a legend
plt.legend()

# Add labels and a title
plt.xlabel('x')
plt.ylabel('y')
plt.title('Region S between $y = x^2$ and $y = 2x$')

# Show the plot with the shaded region
plt.grid(True)
plt.show()
``` &#8203;``【oaicite:0】``&#8203;

```


![[Figure 1.png]]