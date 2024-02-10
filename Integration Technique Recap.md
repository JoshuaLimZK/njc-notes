**Integrate Algebraic Fractions**
$$
\int \frac{x^2 + x - 7}{x^2-x+6} \, dx 
$$
Q1: Is the fraction PROPER
- If no, do LONG DIVISION
$$
\int 1+\frac{2x - 1}{x^2-x-6} \, dx 
$$
Q2: Is there an $f(x) \longleftrightarrow f'(x)$ relationship in the integral
- If yes, Integrate directly
$$
x+\ln |x^2-x-6| +c
$$
- If no,
Q3: Is the denominator FACTORISABLE?
- e.g.
$$
\int 1+\frac{4x-5}{x^2-x-6} \, dx 
$$
- Decompose integrand
$$
\int 1+ \frac{\frac{13}{5}}{(x+2)} + \frac{\frac{7}{5}}{(x-3)} \, dx 
$$
$$
= x + \frac{13}{5}\ln|x+2|+ \frac{7}{5}\ln |x-3|
$$
- If no,
  Try and change nominator such that it is in $f'(x)$ form
  $$
  4x-5 = A(2x-1) + B
  $$
  $$
  \int 1+2\left( \frac{2x-1}{x^2-x-6} \right) - \frac{3}{x^2-x-6} \, dx 
  $$
  - Complete the square for the part with the constant numerator
$$
\int 1+2\left( \frac{2x-1}{x^2-x-6}  \right) - \frac{3}{\left( x-\frac{1}{2} \right)^2 -\left( \frac{5}{2} \right)^2} \, dx 
$$
$$
= x + 2\ln|x^2-x-6| - \frac{3}{2\left( \frac{5}{2} \right)}\ln\left| \frac{  \left( x-\frac{1}{2} \right) -\frac{5}{2}}{\left( x-\frac{1}{2} \right) +\frac{5}{2}}\right|+c
$$
$$
= x + 2\ln|x^2-x-6| - \frac{3}{5}\ln\left| \frac{x-3}{x+2}\right|+c
$$
**For sine, cosine only:** 
Case 1: Total power is odd → use $sin^2 A + cos^2A = 1$
e.g.
$$
\begin{align}
\int \sin^2x\cos^3x \, dx &= \int \sin^2x\cos^2x\cos x \, dx  \\
&=\int \sin^2x(1-\sin^2x)\cos x \, dx  \\
&=\int \sin^2x\cos x-\sin^4x\cos x \, dx  \\
&=\frac{1}{3}\sin^3x -\frac{1}{5}\sin^5x+c
\end{align}
$$
Case 2: Total power is even → use double angle formula

```
	  _______
	/         \
  __|     ____|_
 |  |    |______|
 |  |         |
 |__|         |
	|    |    |
	|____|____|

```

