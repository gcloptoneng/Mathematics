
**Suppose a random variable $X$ represents the heights (in centimeters) of adult males in a certain population. Assume that $X$ is normally distributed with a mean $(\mu)$ of $175 \mathrm{~cm}$ and a standard deviation $(\sigma)$ of $10 \mathrm{~cm}$.**
**1. Calculate the probability that a randomly selected adult male from this population is shorter than $165 \mathrm{~cm}$.**

We are given $\mu=175 \mathrm{~cm}$ and $\sigma=10 \mathrm{~cm}$. We need to find $P(X<165)$. Using the normal distribution function:
$$
P(X \leq x)=\frac{1}{\sigma \sqrt{2 \pi}} \int_{-\infty}^x e^{-\frac{(t-\mu)^2}{2 \sigma^2}} d t
$$

Substituting $x=165, \mu=175$, and $\sigma=10$, the integral becomes:
$$
P(X \leq 165)=\frac{1}{10 \sqrt{2 \pi}} \int_{-\infty}^{165} e^{-\frac{(t-175)^2}{200}} d t
$$

```Python
from scipy.integrate import quad
import numpy as np

# Given values
mu = 175  # mean
sigma = 10  # standard deviation

# Normal distribution function
def normal_distribution(t):
    return (1 / (sigma * np.sqrt(2 * np.pi))) * np.exp(-((t - mu)**2) / (2 * sigma**2))

# Calculating probabilities
# P(X < 165)
prob_less_than_165, _ = quad(normal_distribution, -np.inf, 165)

prob_less_than_165
```

0.15865525393145707


**2. Determine the probability that a randomly selected adult male is taller than $185 \mathrm{~cm}$.**

To find $P(X>185)$, we use the complement rule since $P(X>x)=1-P(X \leq x)$. Thus, we need to calculate $1-P(X \leq 185)$. The integral for $P(X \leq 185)$ is:
$$
P(X \leq 185)=\frac{1}{10 \sqrt{2 \pi}} \int_{-\infty}^{185} e^{-\frac{(t-175)^2}{200}} d t
$$

```Python
# P(X < 185)
prob_less_than_185, _ = quad(normal_distribution, -np.inf, 185)

# P(X > 185) = 1 - P(X < 185)
prob_greater_than_185 = 1 - prob_less_than_185

prob_greater_than_185
```

0.15865525393145596

**3. Find the probability that a randomly selected adult male has a height between $165 \mathrm{~cm}$ and 185 $\mathrm{cm}$.

This is calculated as $P(165<X<185)=P(X<185)-P(X<165)$. We already have the integrals for both parts, so we need to calculate them and then find the difference.

```Python
# P(165 < X < 185) = P(X < 185) - P(X < 165)
prob_between_165_and_185 = prob_less_than_185 - prob_less_than_165

prob_between_165_and_185
```

0.682689492137087

**4. Plot the probability density function (PDF) of the normal distribution and highlight the areas under the curve corresponding to the probabilities you calculated in the previous parts.**


```Python
import matplotlib.pyplot as plt

# Creating a range of values for the x-axis (heights)
x = np.linspace(mu - 4*sigma, mu + 4*sigma, 1000)
y = [normal_distribution(value) for value in x]

# Plotting the PDF of the normal distribution
plt.figure(figsize=(10, 6))
plt.plot(x, y, label="Normal Distribution PDF", color="blue")

# Filling the area under the curve for each scenario
plt.fill_between(x, y, where=(x < 165), color='red', alpha=0.5, label="P(X < 165)")
plt.fill_between(x, y, where=(x > 185), color='green', alpha=0.5, label="P(X > 185)")
plt.fill_between(x, y, where=((x > 165) & (x < 185)), color='yellow', alpha=0.5, label="P(165 < X < 185)")

# Adding labels and title
plt.title("Normal Distribution of Heights with Highlighted Probabilities")
plt.xlabel("Height (cm)")
plt.ylabel("Probability Density")
plt.legend()

# Show the plot
plt.show()

```



1. **Range Creation (x-axis values)**: 
   - `x = np.linspace(mu - 4*sigma, mu + 4*sigma, 1000)`
   - This line creates an array of 1000 values (linearly spaced) between `mu - 4*sigma` and `mu + 4*sigma`.
   - `mu` is the mean of the distribution, and `sigma` is the standard deviation.
   - By choosing `mu - 4*sigma` and `mu + 4*sigma`, you're effectively covering a significant portion of the normal distribution. Most of the area under a normal distribution curve is within four standard deviations from the mean. This range ensures that the curve covers the majority of significant values.

2. **Calculating the y-axis Values**:
   - `y = [normal_distribution(value) for value in x]`
   - This is a list comprehension in Python that calculates the y-axis values for the normal distribution.
   - For each value in the array `x`, the `normal_distribution` function is called to compute the corresponding y-value. 
   - The `normal_distribution` function is presumably defined elsewhere in your code, and it represents the probability density function of a normal distribution.
   - The result is a list `y` containing the density values of the normal distribution for each x-value.
