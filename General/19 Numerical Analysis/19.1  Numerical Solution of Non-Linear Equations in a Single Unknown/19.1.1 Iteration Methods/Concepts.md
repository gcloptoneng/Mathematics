# 19.1 Numerical Solution of Non-Linear Equations in a Single Unknown

## Visual Estimation of Solution

Every equation with one unknown can be transformed into one of the normal forms:
Zero form: $\quad f(x)=0$.
Fixed point form: $x=\varphi(x)$.

1. Zero Form: $f(x)=0$
This form is typically used for solving equations where you set the entire equation to zero and then find the value of $x$ that satisfies this condition.
Example: $x^2-4=0$
In this case, $f(x)=x^2-4$. To solve it, you would find the values of $x$ that make $x^2-4=0$.
2. Fixed Point Form: $x=\varphi(x)$
This form is used in iterative methods for solving equations. You rewrite the equation such that $x$ is explicitly expressed as a function of $x$ on the other side.
Example: $x^2-x-2=0$
To convert this into the fixed point form, you might rearrange it to $x=1+\sqrt{2+x}$. Here, $\varphi(x)=1+\sqrt{2+x}$. The solution is found by iteratively plugging in estimates of $x$ into the right-hand side until the value of $x$ converges.

Suppose equations (19.1) and (19.2) can be solved. The solutions are denoted by $x^*$. To get a first approximation of $x^*$, we can try to transform the equation into the form $f_1(x)=f_2(x)$, where the curves of the functions $y=f_1(x)$ and $y=f_2(x)$ are more or less simple to sketch.


##### Problem

Given $x^2-x-6=0$, find the first approximation of the solution $x^*$ for the given equation by transforming it into the form $f_1(x)=f_2(x)$ and plotting the functions.

##### Problem
Given , find the first approximation of the solution $x^*$ for the given equation by transforming it into the form $f_1(x)=f_2(x)$ and plotting the functions.


## Iteration Method

The general idea of iterative methods is that starting with known initial approximations $x_k(k=$ $0,1, \ldots, n)$ a sequence of further and better approximations is formed, step by step, hence the solution of the given equation is approached by iteration, by a convergent sequence. A sequence is tried to be created with convergence as fast as possible.

### Ordinary Iteration Method

To solve an equation given in or transformed into the fixed point form $x=\varphi(x)$, the iteration rule $x_{n+1}=\varphi\left(x_n\right) \quad\left(n=0,1,2, \ldots ; x_0\right.$ given $)$
is used which is called the ordinary iteration method. It converges to a solution $x^*$ if there is a neighborhood of $x^*$ (Fig. 19.2) such that
$$
\left|\frac{\varphi(x)-\varphi\left(x^*\right)}{x-x^*}\right| \leq K<1 \quad(K \text { const })
$$
holds, and the initial approximation $x_0$ is in this neighborhood. 




#### Convergence Criterion

If $\varphi(x)$ is differentiable, then the corresponding condition is
$$
\left|\varphi^{\prime}(x)\right| \leq K<1 .
$$

The convergence of the ordinary iteration method becomes faster with smaller values of $K$.



