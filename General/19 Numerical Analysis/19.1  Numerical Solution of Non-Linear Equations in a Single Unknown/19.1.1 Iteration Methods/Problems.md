Consider the function $\varphi(x)=\cos (x)$. Your task is to find a fixed point $x^*$ of this function, i.e., a point where $x^*=\varphi\left(x^*\right)$, using the ordinary iteration method.
1. Start with an initial guess $x_0$. For simplicity, let's take $x_0=1$.
2. Apply the iteration rule $x_{n+1}=\varphi\left(x_n\right)$, which in this case becomes $x_{n+1}=\cos \left(x_n\right)$.
3. Continue the iterations until the difference between successive approximations is smaller than a given tolerance, say $10^{-5}$.
4. Verify the convergence condition $\left|\frac{\varphi(x)-\varphi\left(x^*\right)}{x-x^*}\right| \leq K<1$ in the neighborhood of the computed $x^*$.