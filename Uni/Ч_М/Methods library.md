#n_m 
# Floating point representation
IEEE 754
$\frac{s}{b^{p-1}} \times b^e$, where $s$ - significand, b - base (in computers b = 2), p - precision

For computers we have following boundaries for number representation:
$0 < X_0 \leq |x| < X_{\infty}$, where $X_0 = 2^{-p_{max} + 1}$ and $X_{\infty} = 2^{p_{max}}$
# Upper bound of positive polynomial roots theorem
Given $\displaystyle P_n(x) = \sum_{i = 0}^n a_i x^i$, such that $a_n > 0$:
$\displaystyle \forall x^* > 0: P_n(x^*) = 0 \Rightarrow x^* \leq 1 + \sqrt[m]{\frac{|a'|}{a_n}}$, 
where $m$ is the number of the first negative number in $a_{n-1}, a_{n-2}, ...$, and $a'$ is the biggest negative coefficient by an absolute value.
**Proof**


**Note:** lower bound of positive roots and upper and lower boundaries of negative root can be found by following substitutions: $x = 1/t, \ x = -t, \ x = -1/t$ 
# The Bisection method
## Algorithm
while $|b-a| > 2\varepsilon$
	$c = \frac{|b-a|}{2}$
	if $f(a)f(b) < 0$
		$b = c$
	else 
		$a = c$
$x = \frac{a+b}{2}$
## Conditions of applicability
1. $f \in C([a,b])$
2. $f(a)f(b) < 0$
# Newton's method
$x^{(k+1)} = x^{(k)} - \frac{f(x^{(k)})}{f'(x^{(k)})}$
## Newton's method convergence theorem
Consider:
1. $f \in C^{(2)}([a, b])$
2. $f(a)f(b) < 0$
3. $f'$ and $f''$ are of constant signs
4. first approximation $x^{(0)}$ satisfies: $f(x^{(0)})f''(x^{(0)}) > 0$ (Fourier's condition)
Then $\{x^{(n)}\}^{\infty}_{n = 0}$ converges to the solution $x^* \in (a, b)$

**Proof**
$f(x^*) = f(x^{(0)}) + f'(x^{(0)})(x^* - x^{(0)}) + \frac{f''(x^{(0)})}{2}(x^* - x^{(0)})^2 \Rightarrow$ 
$\Rightarrow f(x^{(0)}) + f'(x^{(0)})(x^* - x^{(0)}) < 0 \Rightarrow$ 
$\Rightarrow x^* < x^{(0)} - \frac{f(x^{(0)})}{f'(x^{(0)})} = x^{(1)} < x^{(0)}$ and $f(x^{(1)}) > 0$

By induction: 
$\forall k \in \mathbb{N}: \ x^* < x^{(k+1)} < x^{(k)} \Rightarrow \exists \ \underset{k \to \infty}{\lim} x^{(k)}$

Approaching limits from left and right:
$\overline{x} = \overline{x} - \frac{f(\overline{x})}{f'(\overline{x})} \Rightarrow f(\overline{x}) = 0$ and $\overline{x}$ is the root. $\square$
## Newton's method rate of convergence theorem
Consider $m_1 = \underset{x \in [a, b]}{\min}|f'(x)| > 0$ and $M_2 = \underset{x \in [a, b]}{\max}|f''(x)| < \infty$ for any $x \in [a, b]$
If $\underset{k \to \infty}{\lim}x^{(k)} = x^*$ then $\forall k \in \mathbb{N}$:
$|x^* - x^{(k+1)}| \leq \frac{M_2}{2m_1}(x^* - x^{(k)})^2$
$|x^* - x^{(k+1)}| \leq \frac{M_2}{2m_1}(x^{(k+1)} - x^{(k)})^2$

**Proof**
Taylor series:
$f(x^{(k)}) +f'(x^{(k)})(x^* - x^{(k)}) + \frac{f''(\xi_k)}{2}(x^* - x^{(k)})^2 = 0$

Newton's formula:
$f(x^{(k)}) +f'(x^{(k)})(x^{(k+1)} - x^{(k)}) \Rightarrow x^* - x^{(k+1)} = - \frac{f''(\xi_k)}{2f'(x^{(k)})}(x^* - x^{(k)})^2$

$|x^* - x^{(k+1)}| = \frac{1}{2}\left|\frac{f''(\xi_k)}{f'(x^{(k)})}\right|(x^* - x^{(k)})^2 \leq \frac{M_2}{2m_1}(x^* - x^{(k)})^2$

$f(x^{(k)}) = f(x^{(k+1)}) +f'(x^{(k)})(x^{(k+1)}- x^{(k)}) + \frac{f''(\tilde{\xi_k)}}{2}(x^{(k+1)} - x^{(k)})^2$
$f(x^{(k)}) = \frac{f''(\tilde{\xi_k)}}{2}(x^{(k+1)} - x^{(k)})^2$
$|f(x^{(k)})| \leq \frac{M_2}{2}(x^{(k+1)} - x^{(k)})^2$

Lagrange's formula:
$f(x^*) - f(x^{(k+1)}) = f'(\tau)(x^*)(x^* - x^{(k+1)})$

$|x^* - x^{(k+1)}| = \left|\frac{f^{(k+1)}}{f'(\tau)}\right| \leq \frac{M_2}{2m_1}(x^{(k+1)} - x^{(k)})^2$ $\square$


## Newton's method for multiple root
$x^{(k+1)} = x^{(k)} - m\frac{f(x^{(k)})}{f'(x^{(k)})}$, where $m$ is the multiplicity of a root
## Modified Newton's method
$x^{(k+1)} = x^{(k)} - \frac{f(x^{(k)})}{f'(x^{(0)})}$
This modification reduces the time of iteration, but the rate of convergence reduces too.

# Secant method
Give up computation of $f'(x^{(k)})$ and substitute it with
$f'(x^{(k)}) = \frac{f(x^{(k)}) - f(x^{(k-1)})}{x^{(k)} - x^{(k-1)}}$
Secant method formula:
$x^{(k+1)} = x^{(k)} - f(x^{(k)})\frac{x^{(k)} - x^{(k-1)}}{f(x^{(k)}) - f(x^{(k-1)})}$
## Notes
1. It is a two-step method
2. On a first step takes two points that satisfy the Fourier condition
3. One iteration of a secant method needs only one computation of a value of a function $f$, while Newton's method takes two ($f$ and $f'$), but the rate of convergence is lower than the Newton's method
4. Starting from definite $k$ errors start to get high because of subtraction of close values

# Chord method
A straight line is drawn connecting the two extreme points (chord). We select the interval which contain the root.
## Chord method's convergence theorem 
Consider:
1. $f \in C^{(2)}([a,b])$
2. $f(a)f(b) < 0$
3. $f'$ and $f''$ are of constant sign on $[a, b]$
4. for starting point $x^{(0)}$: $f(x^{(0)})f''(x^{(0)}) < 0$
5. for fixed point $\overline{x}$: $f(\overline{x})f''(\overline{x}) > 0$
Then:
1. sequence $x^{(k+1)} = x^{(k)} - f(x^{(k)})\frac{x^{(k)} - \overline{x}}{f(x^{(k)})- f(\overline{x})}$ converges
2. fair estimate of error: $|x^* - x^{(k+1)}| \leq \frac{M_1 - m_1}{m_1}|x^{(k+1)} - x^{(k)}|$, where $M_1 = \underset{x \in [a,b]}{\max}|f'(x)|$ and $m_1 = \underset{x \in [a,b]}{\min}|f'(x)|$

## Notes
1. Chord method works fast for linear-like functions because for linear function this method gets solution in one iteration
2. Chord method and Newton's method approach the root from different directions $\Rightarrow$ we can find the root with both methods without any error estimations and using only interval reduction as in bisection method. Keep in mind that fixed point changes with every iteration
# Inverse quadratic interpolation
Idea: approximating function with parabola $x(y)$ 
Let $f_k = f(x^{(k)})$
The parabola equation that contains points $(f_{k-2}, x^{(k-2)}), (f_{k-1}, x^{(k-1)})$ and $(f_{k}, x^{(k)})$:
$x(y) = x^{(k-2)}\frac{(y - f_{k-1})(y - f_k)}{(f_{k-2} - f_{k-1})(f_{k-2} - f_k)} + x^{(k-1)}\frac{(y-f_{k-2})(y-f_k)}{(f_{k-1} - f_{k-2})(f_{k-1} - f_k)} + x^{(k)}\frac{(y - f_{k-2})(y - f_{k-1})}{(f_k - f_{k-1})(f_k - f_{k-2})}$

Recurrent formula:
$x^{(k+1)} = x^{(k-2)}\frac{f_{k-1}f_{k}}{(f_{k-2} - f_{k-1})(f_{k-2} - f_k)} + x^{(k-1)}\frac{f_{k-2}f_k}{(f_{k-1} - f_{k-2})(f_{k-1} - f_k)} + x^k\frac{f_{k-2}f_{k-1}}{(f_k - f_{k-2})(f_k - f_{k-1})}$

**Note:** if any two values matched, further interpolation is impossible
# Rate of conversion of iterative process
**Def:** progression $\{x^{(k)}\}$ converges to $x^*$ at rate at least of $p$ if $\exists C > 0, p \geq 1: |x^* - x^{(k+1)}| \leq C|x^* - x^{(k)}|^p$ starting from $k = k_0 \in \mathbb{N}$

# Fixed point iterations
Consider $f(x) = 0$ such that $x \in [a, b], f \in C([a, b]), f(a)f(b) < 0$
Suppose that we can rewrite initial equation to $x = \varphi(x)$. Let's suppose that $\varphi \in C([a, b])$.
Construct the sequence $\{x^{(k)}\}$ with recurrent formula: $x^{(k+1)} = \varphi(x^{(k)})$
If this sequence converges to $x^*$ then $x^*$ is the root of the initial equation.
## Rate of convergence of fixed point iterations first theorem 
Let:
1. $\varphi \in C^{(1)}([a,b])$
2. $\forall x \in [a,b]: \varphi(x) \in [a, b]$
3. $\exists q \in (0, 1): \forall x \in [a, b] \ |\varphi'(x)| \leq q$
Then:
1. $x = \varphi(x)$ has only one root $x^*$ on $[a, b]$
2. $x^*$ is the limit of a recurrent progression $x^{(k+1)} = \varphi(x^{(k)})$
3. Estimate error: $|x^* - x^{(k)}| \leq \frac{q}{1-q}|x^{(k)} - x^{(k-1)}|$
This theorem is hard to use in practice
## Rate of convergence of fixed point iterations second theorem 
Let:
1. $\varphi \in C^{(1)}([a,b])$
2. $\forall x \in [a,b]: \varphi(x) \in [a, b]$
3. $x^* \in [\alpha, \beta] \subset[a, b]$, where $\alpha = a + \frac{b-a}{3}$, $\beta = b - \frac{b-a}{3}$
Then $\forall x^{(0)} \in [\alpha, \beta]$:
1. $x^*$ is the limit of a recurrent progression $x^{(k+1)} = \varphi(x^{(k)})$
2. Estimate error: $|x^* - x^{(k)}| \leq \frac{q}{1-q}|x^{(k)} - x^{(k-1)}|$
**Proof:**
Let $\overline{S}(x^*, \delta) := [x^* - \delta, x^* + \delta]$, where $\delta = \frac{b-a}{3}$. $\overline{S}(x^*, \delta) \subset [a, b]$
We will show that $\varphi$ maps $\overline{S}$ on itself.
Let $x' \in \overline{S}$ and $x'' = \varphi(x')$
Then $|x'' - x^*| = \varphi(x') - \varphi(x^*)| = |\varphi'(\xi)||x' - x^*| \leq q\delta \leq \delta \Rightarrow x'' \in \overline{S}$
This satisfies the conditions of first theorem $\Rightarrow \underset{k \to \infty}{\lim}x^{(k)} = x^*$$x^{(k+1)} - x^{(k)} = \varphi(x^{(k)}) - \varphi(x^*) + \varphi(x^*) - x^{(k)} = \varphi'(\xi)(x^{(k)} - x^*) - (x^{(k)} - x^*) = (\varphi'(\xi) - 1)(x^{(k)} - x^*)$
$|x^{(k)} - x^*| = \frac{1}{\varphi'(\xi) - 1}|x^{(k+1)} - x^{(k)}| \leq \frac{1}{1-q}|\varphi(x^{(k)}) - \varphi(x^{(k-1)})| \leq \frac{q}{1-q}|x^{(k)} - x^{(k-1)}|$
$\square$

## How to rewrite the equation for iterations?
Let $f'$ be the continuous and of constant sign on $[a, b]$
$f(x) = 0 \Leftrightarrow x = x -\alpha f(x), \ \alpha \neq 0$ in other words $\varphi(x) = x - \alpha f(x)$.
$|\varphi'(x)| < 1 \Leftrightarrow -1 < 1 - \alpha f'(x) < 1 \Leftrightarrow 0 < \alpha f'(x) < 2 \Rightarrow sign(\alpha) = sign(f'(x))$ and $|\alpha| = 2/M_1$
if $\alpha = \alpha(k)$ then process is non-stationary, if not - process is stationary.
# Wegstein's method
Let $\overline{x}^{(k)}$ be the $k$ iteration of a Wegstein's method and $x^{(k+1)} = \varphi(x^{(k)})$ be the fixed point iteration.

Geometrically the fixed point iterations is a method of finding intersection of $y = x$ and $y = \varphi(x)$. 

Let's draw a horizontal line from a point $(\overline{x}^{(k)}, \varphi(\overline{x}^{(k)}))$ and intersection point $A$ with $y = x$ will be our $x^{(k+1)}$. Let point $P$ be the $(x^*, \varphi(x^*))$, $A$ and $C$ be the point of intersection of vertical line which contains $P$ and horizontal line which contains $A$.

Since $PC = AC \Rightarrow \varphi(x^*) - \varphi(\overline{x}^{(k)}) = \varphi'(\theta_k)(x^* - \overline{x}^{(k)}) = x^* - x^{(k+1)} \Rightarrow x^* = x^{(k+1)} - \frac{x^{(k+1)} - \overline{x}^{(k)}}{1 - \frac{1}{\varphi'(\theta_k)}}$
$\varphi'(\theta_k) \approx \frac{\varphi(\overline{x}^{(k)}) - \varphi(\overline{x}^{(k-1)})}{\overline{x}^{(k)} - \overline{x}^{(k-1)}} = \frac{x^{(k+1)} - x^{(k)}}{\overline{x}^{(k)} - \overline{x}^{(k-1)}}$
$\overline{x}^{(k+1)} = \frac{x^{(k+1)}\overline{x}^{(k-1)} - x^{(k)}\overline{x}^{(k)}}{x^{(k+1)} +\overline{x}^{(k-1)} - x^{(k)} - \overline{x}^{(k)}}$
# Aitken's acceleration
Consider sequence with linear rate of conversion:
$\alpha_k = \alpha_0 + \beta^k\gamma, \ |\beta| < 1$
Obviously, $\underset{k \to \infty}{\lim} \alpha_k = \alpha_0$
It is possible to compute $\alpha_0$ knowing three sequential elements:
$\beta^k = \frac{\alpha_k - \alpha_0}{\gamma} \Rightarrow \beta = \frac{\alpha_k - \alpha_0}{\alpha_{k-1} - \alpha_0} = \frac{\alpha_{k+1} - \alpha_0}{\alpha_{k} - \alpha_0}$
Then we have $\alpha_0 = \frac{\alpha_k^2 - \alpha_{k+1}\alpha_{k-1}}{2\alpha_k - \alpha_{k+1} - \alpha_{k-1}}$ (\*)

Let's return to iteration process:
$x^{(k)} = x^* + \epsilon(k), \ \epsilon(k) \underset{k \to \infty}{\longrightarrow} 0$ (\*\*)

Using Taylor series:
$x^{(k)} = \varphi(x^{(k-1)}) = \varphi(x^*) + \varphi'(x^*)\epsilon^{(k-1)} + \frac{\varphi''(x^*)}{2}(\epsilon^{(k-1)})^2 + \ldots$ (\*\*\*)

Refuse non-linearity in (\*\*) and knowing (\*) and $x^* = \varphi(x^*)$:
$\epsilon^{(k)} \approx \varphi'(x^*)\epsilon^{(k-1)} \approx (\varphi'(x^*))^2\epsilon^{(k-2)} \approx \ldots \approx (\varphi'(x^*))^k\epsilon^{(0)}$

Therefore
$x^{(k)} \approx x^* + (\varphi'(x^*))^k\epsilon^{(0)}$ and $|\varphi'(x^*)| < 1$

Applying (\*) to initial sequence:

$\tilde{x}^{(k+1)} = \frac{(x^{(k)})^2 - x^{(k+1)}x^{(k-1)}}{2x^{(k)} - x^{(k+1)} - x^{(k-1)}}$ (1)

## Algorithm
given $x^{(0)}, \ x^{(1)} = \varphi(x^{(0)}), \ x^{(2)} = \varphi(x^{(1)})$

while true
	compute $\tilde{x}^{(2)}$ with formula (1)
	if $|x^{(3)} - \tilde{x}^{(2)}| > \frac{1-q}{q}\varepsilon$
		$x^{(0)} = \tilde{x}^{(2)}, \ x^{(1)} = x^{(3)}$
		$x^{(2)} = \varphi(x^{(1)})$
	else
		break

# Thomas algorithm
We will call a *tridiagonal* matrix $(a_{ij})_{n \times n}$ with following property:
$a_{ij} = \left\{ \begin{array}{rcl} 0 & \mbox{if} & |i - j| > 1 \\ a_{ij} & \mbox{if} & |i-j| \leq 1 \end{array}\right.$
Therefore, in every row we have an equation with 3 variables:
$b_ix_{i-1} + c_ix_i + d_ix_{i+1} = r_i$, (\*) where $b_i$ is a lower diagonal, $c_i$ is a central diagonal, $d_i$ is an upper diagonal and $r_i$ is a column element.

Let $\exists \delta_i, \ \lambda_i:$
$x_i = \delta_ix_{i+1} + \lambda_i, \ i = 1, \ldots, n$ (\*\*)
(\*\*) $\to$ (\*):
$b_i(\delta_{i-1}x_i + \lambda_{i-1}) + c_ix_i + d_ix_{i+1} = r_i \Rightarrow x_i = -\frac{d_i}{b_i\delta_{i-1} + c_i}x_{i+1} + \frac{r_i - b_i\lambda_{i-1}}{b_i\delta_{i-1} + c_i}$

We got a recurrent formulas for $\delta_i$ and $\lambda_i$:
$\delta_i = -\frac{d_i}{b_i\delta_{i-1} + c_i}, \ \lambda_i = \frac{r_i - b_i\lambda_{i-1}}{b_i\delta_{i-1} + c_i}, \ i = 1, \ldots, n$

## Algorithm
### Forward sweep
$i = 1: \ b_1 = 0 \Rightarrow \delta_1 = -\frac{d_1}{c_1}, \ \lambda_1 = \frac{r_1}{c_1}$
for $i = 2, \ldots, n-1$ works recurrent formula
for $i = n: \ d_n = 0 \Rightarrow \delta_i = 0, \ \lambda_n = \frac{r_n - b_n\lambda_{n-1}}{b_n\delta_{n-1} + c_n}$
### Back substitution
$i = n: \ x_n = \lambda_n$
for $i = n-1, \ldots, 1$ works formula (\*)

Some problems may appear in this algorithm:
1. division by zero in recurrent formulas
2. if $|\delta_i| > 1$ it is possible to come across increasing error in formula (\*\*)

This method will work properly if we demand $|c_i| > |b_i| + |d_i|, \ i = 1, \ldots, n$

# Gaussian method
I will not fully write this method as I've executed it successfully in lab. I will only make some notes about conditions.

**Condition of applicability:** Every main minor of a matrix must $\neq 0$

## Algorithm
for $k = 1, \ldots, n-1$
	find $m \geq k: \ |a_{km}| = \underset{i \geq k}{\max}\{|a_{ki}|\}$
	if $|a_{km}| < \varepsilon$:
		break
	else:
		swap columns $k$ and $m$
	for $i = k+1, \ldots, n:$
		$t_{ik} = a_{ik}/a_{kk}$
		$b_i = b_i - t_{ik}b_k$
		for $j = k+1, \ldots, n:$
			$a_{ij} = a_{ij} - t_{ik}a_{kj}$
$x_n = b_n/a_{nn}$
return columns back to places
for $k = n-1, \ldots, 1:$
	$x_k = (b_k - \sum_{j = k+1}^{n}a_{kj}x_j)/a_{kk}$

This algorithm contains modification which finds the maximum element in column and brings it to leading position. The same can be done with search in rows. This adds $O(n^2)$ operations which is not affects the method radically since it works in $O(n^3)$. We can even search through the whole matrix for the leading element, but it will cost $O(n^3)$ operations which totally affect the speed of method.
# Condition of a problem
## Matrix norm
**Def:** $\|A\| = \underset{x \neq 0}{\max}\frac{\|Ax\|}{\|x\|} = \underset{\|y\| = 1}{\max}\|Ay\|$
**Properties:**
1. $\forall A, x: \ \|Ax\| \leq \|A\| \|x\|$
2. $\forall A, B: \ \|AB\| \leq \|A\| \|B\|$
**Examples:**
1. $\|A\|_1 = \underset{1 \leq j \leq n}{\max}\sum_{i = 1}^n |a_{ij}|$
2. $\|A\|_{\infty} = \underset{1 \leq i \leq n}{\max}\sum_{j = 1}^n |a_{ij}|$
3. $\|A\|_F = \sqrt{\sum_{i, j = 1}^n a_{ij}^2}$
4. 
## Condition number of a matrix
$Ax = b \longrightarrow A(x+\delta x) = b + \delta b$
$\|b\| \leq \|A\| \|x\|, \ \|\delta x\| \leq \|A^{-1} \| \| \delta b\| \Rightarrow \|b\| \| \delta x\| \leq \|A\| \|x\| \|A^{-1}\| \| \delta b\|$

$\frac{\| \delta x \|}{\| x \|} \leq \|A\| \|A^{-1}\|  \frac{\| \delta b\|}{\| b \|} = cond(A) \frac{\| \delta b\|}{\| b \|}$
**Def:** the condition number of a matrix A: $cond(A) = \|A\| \|A^{-1}\|$
**Properties**
1. $cond(E) = 1$
2. $cond(A) \geq 1$: $E = AA^{-1}, \ 1 \leq \|A\| \|A^{-1}\|$
3. $cond(\alpha A) = cond(A)$: $(\alpha A)^{-1} = \frac{1}{\alpha} A^{-1}$
### Hilbert matrix
$h_{ij} = \frac{1}{i+j-1}$
This matrix is ill-conditioned
# LDR decomposition
$\forall A \in M_n(\mathbb{R}) \det A \neq 0 \Rightarrow \exists ! x \in \mathbb{R}: Ax = b$ 

$Ax = b \Leftrightarrow L(D(Rx)) = b \Leftrightarrow \left\{ \begin{array}{rcl} Lz = b & forward \ sweep & \ \\ Dy = z & \ & \ \\ Rx = y & back \ substitution & \ \end{array}\right.$
**Theorem:**
If all main minors of $A$ do not equal to zero then $\exists ! \ L, \ D, \ R$ such that
$A = LDR$, 
where $L$ is a lower triangular matrix with ones on a diagonal, $D$ is a diagonal matrix and $R$ is a upper triangular matrix with ones on a diagonal.

## Algorithm
$A = LDR \Leftrightarrow a_{ij} = \sum_{k =1}^{n} l_{ik}d_kr_{kj}$
### First step
$a_{11} = l_{11}d_1r_{11} = d_1$
$j > 1: \ a_{1j} = l_{11}d_1r_{1j} + \textcolor{red}{l_{12}}d_2r_{2j} + \ldots = l_{11}d_1r_{1j} \Rightarrow r_{1j} = \frac{a_{1j}}{d_1}$
$i > 1: \ a_{i1} = l_{i1}d{1}r_{11} + l_{i2}d_2\textcolor{red}{r_{21}} + \ldots = l_{i1}d{1}r_{11} \Rightarrow l_{i1} = \frac{a_{i1}}{d_1}$
### m-th step
$a_{mm} = \sum_{k = 1}^{m-1} l_{mk}d_mr_{km} + l_{mm}d_mr_{mm} + 0 \Rightarrow d_m = a_{mm} - \sum_{k = 1}^{m-1} l_{mk}d_mr_{km}$

$j > m: \ a_{mj} = \sum_{k = 1}^{m-1} l_{mk}d_mr_{kj} + l_{mm}d_mr_{mj} + 0 \Rightarrow r_{mj} = \frac{a_{mj} - \sum_{k = 1}^{m-1} l_{mk}d_mr_{kj}}{d_m}$

$i > m: \ a_{im} = \sum_{k = 1}^{m-1} l_{ik}d_mr_{km} + l_{im}d_mr_{mm} + 0 \Rightarrow l_{im} = \frac{a_{im} - \sum_{k = 1}^{m-1} l_{ik}d_mr_{km}}{d_m}$

**Computational complexity:** $O(n^3)$ (approximately $\frac{2n^3}{3}$)
# LDL^t decomposition
$A = {^t}A \Rightarrow R = {^t}L$, so computational complexity drops two times since $r_{ij} = l_{ji}$
# LU decomposition
## Theorem 
Let $A \in \mathbb{R}^{n \times n}$. If every main minor of A is not equal to zero, then
$\exists ! \ L, U: \ A = LU$, where $L$ is a lower triangular matrix with ones on the diagonal and $U$ is an upper triangular matrix
**Proof:**
*Base:* $L = 1, \ U = a_{11}$
*Induction transition:* 
Suppose for $A_{k-1}$ exists only one LU decomposition
$A_{k-1} = L_{k-1}U_{k-1}$

$A_k = \begin{bmatrix} A_{k-1} & f_{k-1} \\ {^t}g_{k-1} & a_{kk} \end{bmatrix}$, $L_k = \begin{bmatrix} L_{k-1} & 0 \\ \textcolor{red}{{^t}x_{k-1}} & 1 \end{bmatrix}$, $U_k = \begin{bmatrix} U_{k-1} & \textcolor{red}{y_{k-1}} \\ 0 & \textcolor{red}{u_{kk}} \end{bmatrix}$,
where $f_{k-1}, g_{k-1} \in \mathbb{R}^{n-1}$ are known, $0 \in \mathbb{R}^{n-1}, \ x_{k-1}, y_{k-1} \in \mathbb{R}^{n-1}$ - we need to find.

$A_k = \begin{bmatrix} A_{k-1} & f_{k-1} \\ {^t}g_{k-1} & a_{kk} \end{bmatrix} = L_kU_k = \begin{bmatrix} L_{k-1}U_{k-1} & L_{k-1}y_{k-1} \\ {^t}x_{k-1}U_{k-1} & {^t}x_{k-1}y_{k-1}+u_{kk} \end{bmatrix}$
$\Leftrightarrow (A_{k-1} = L_{k-1}U_{k-1}) \wedge (f_{k-1} = L_{k-1}y_{k-1}) \wedge ({^t}g_{k-1} = {^t}x_{k-1}U_{k-1}) \wedge (a_{kk} = {^t}x_{k-1}y_{k-1} + u_{kk})$

$\det(L_{k-1}) \neq 0 \Rightarrow \exists ! y_{k-1}$,
$\det(U_{k-1}) \neq 0 \Rightarrow \exists !x_{k-1}$
Therefore, everything is found.
$\square$
## Algorithm
### First step
$j \geq 1: \ a_{1j} = l_{11}u_{1j} + \textcolor{red}{l_{12}}u_{2j} + \ldots  \Rightarrow u_{1j} = a_{1j}$
$i > 1: \ a_{i1} = l_{i1}u_{11} + l_{i2}\textcolor{red}{u_{21}} + \ldots \Rightarrow l_{i1} = \frac{a_{i1}}{u_{11}}$
### m-th step
$j \geq m: \ a_{mj} = \sum_{k = 1}^{m-1} l_{mk}u_{kj} + l_{mm}u_{mj} + 0 \Rightarrow u_{mj} = a_{mj} - \sum_{k = 1}^{m-1} l_{mk}u_{kj}$

$i > m: \ a_{im} = \sum_{k = 1}^{m-1} l_{ik}u{km} + l_{im}u_{mm} + 0 \Rightarrow l_{im} = \frac{a_{im} - \sum_{k = 1}^{m-1} l_{ik}u_{km}}{u_{mm}}$
# The Cholesky factorisation
**Def:** symmetrical matrix $A \in \mathbb{R}^{n \times n}$ is called *positive definite* if $\forall x \in \mathbb{R}^n: \  {^t}xAx > 0$

**Theorem:** Let $A \in \mathbb{R}^{n \times n}$ be a symmetrical positive definite matrix
Then $\exists ! \ S: \ A = S \cdot {^t}S$, where $S$ is a lower triangular matrix.
## Algorithm

$A = S \cdot {^t}S \Leftrightarrow a_{ij} = \sum_{k = 1}^n s_{ik}s_{jk}$
### First step
$a_{11} = s_{11}^2 + \textcolor{red}{s_{12^2}} + \ldots  \Rightarrow s_{11} = \sqrt{a_{11}}$
$j > 1: \ a_{1j} = s_{11}s_{j1} + \textcolor{red}{s_{12}s_{j2}} + \ldots \Rightarrow s_{j1} = \frac{a_{1j}}{s_{11}}$
### m-th step
$a_{mm} = \sum_{k = 1}^{m-1} s_{mk}^2 + s_{mm}^2 + \sum_{k = m + 1}^n \textcolor{red}{s_{mk}^2} \Rightarrow s_{mm} = \sqrt{a_{mm} - \sum_{k = 1}^{m-1} s_{mk}^2}$

$j > m: \ a_{mj} = \sum_{k = 1}^{m-1} s_{mk}s_{jk} + s_{mm}s_{jm} + 0 \Rightarrow s_{jm} = \frac{a_{mj} - \sum_{k = 1}^{m-1} s_{mk}s_{jk}}{s_{mm}}$
# LUP decomposition
**Def:** The *permutation matrix* $P$ comes from swapping rows of the identity matrix $E$ and applied to a matrix $A$ swaps its corresponding rows

LU decomposition works for not any matrix $A$ with non zero determinant.
For better stability of LU decomposition we can use the permutation matrix.

$PA = LU \Rightarrow LUx = Pb$
# Orthogonalization
Let $A \in \mathbb{R}^{n \times n}$ and $\det A \neq 0$. Then
$A = QR$, 
where ${^t}Q = Q^{-1}$ and $R$ is upper triangular matrix.

$Ax = b \Leftrightarrow QRx = b \Leftrightarrow Rx = {^t}Qb$
Therefore, we reduced the original problem to "R problem"

**Scalar product and norm in** $\mathbb{R}^n$
$(x, y) = \sum_{i = 1}^n x_iy_i$, $\|x\|^2 = (x, x)$

We call $x$ and $y$ *orthogonal* when $(x, y) = 0$.

**Projection of vector a on vector b**
$proj_ba = \frac{(a,b)}{(b,b)}b$
# Gram–Schmidt process
$\det A \neq 0 \Rightarrow$ all columns are linearly independent.
Let $A = [a^{(1)}a^{(2)}\ldots a^{(n)}]$, where $a^{(k)}$ is a column of number $k$ of $A$
These columns create basis in n-dimensional space.
We will create orthonormal basis $q^{(1)}, q^{(2)}, \ldots, q^{(n)}$ based on $a^{(1)},a^{(2)},\ldots, a^{(n)}$

## Algorithm
**First vector**
$u^{(1)} = a^{(1)}$, $q^{(1)} = \frac{u^{(1)}}{\|u^{(1)}\|} = \rho_{11}a^{(1)}$

**Second vector**
$u^{(2)} = a^{(2)} - proj_{q^{(1)}}a^{(2)} = a^{(2)} - (a^{(2)}, q^{(1)})q^{(1)}$
$q^{(2)} = \frac{u^{(2)}}{\|u^{(2)}\|} = \rho_{22}a^{(2)} - \rho_{21}a^{(1)}$
*Note:* here and everywhere $\rho_{ij}$ are elements of upper triangular matrix $R^{-1}$ as following is true:
$[q^{(1)}q^{(2)}\ldots q^{(n)}] = [a^{(1)}a^{(2)}\ldots a^{(n)}]R^{-1}$.
In $\rho_{ij}$ $i$ is the number of column, $j$ is the number of row.

**Third vector**
$u^{(3)} = a^{(3)} - proj_{q^{(1)}}a^{(3)} - proj_{q^{(2)}}a^{(3)} = a^{(3)} - (a^{(3)}, q^{(1)})q^{(1)} - (a^{(3)}, q^{(2)})q^{(2)}$
$q^{(3)} = \rho_{33}a^{(3)} - \rho_{32}a^{(2)} - \rho_{31}a^{(1)}$

Suppose $q^{(1)}, q^{(2)}, \ldots, q^{(i-1)}$ are already constructed:

$q^{(j)} = \sum_{k = 1}^j \rho_{jk} a^{(k)}, \ j, k < i$

We will construct $q^{(i)}$:
$u^{(i)} = a^{(i)} - \sum_{j = 1}^{i - 1} proj_{q^{(j)}} a^{(i)} = a^{(i)} - \sum_{j = 1}^{i - 1} (a^{(i)}, q^{(j)})q^{(j)} = a^{(i)} - \sum_{j = 1}^{i - 1} \gamma_{ij}q^{(j)}$

$q^{(i)} = \frac{u^{(i)}}{\|u^{(i)}\|} = \rho_{ii}a^{(i)} - \rho_{ii}\sum_{j = 1}^{i-1} \gamma_{ij}\left(\sum_{k=1}^{j} \rho_{jk}a^{(k)} \right) = \rho_{ii}a^{(i)} + \sum_{k = 1}^{i-1} \left( -\rho_{ii} \sum_{j = k}^{i - 1} \gamma_{ij}\rho_{jk} \right) a^{(k)}$

Therefore we have $q^{(i)} = \sum_{k=1}^i \rho_{ik}a^{(k)}$, where $\rho_{ik} = -\rho_{ii} \sum_{j = k}^{i-1} \gamma_{ij}\rho_{jk}$, $k < i$

Let $Q = [q^{(1)}q^{(2)}\ldots q^{(n)}]$
The solution of initial problem: $x =R^{-1}\cdot {^t}Qb = R^{-1}\cdot{^t}(AR^{-1})b$.

## Modification
Instead of direct computation of $u^{(i)}$:
$a_1^{(i)} = a^{(i)} - proj_{q^{(1)}}a^{(i)}$
$a_2^{(i)} = a_1^{(i)} - proj_{q^{(2)}}a_1^{(i)}$
$\vdots$
$a_{i-1}^{(i)} = a_{i-2}^{(i)} - proj_{q^{(i-1)}}a_{i-2}^{(i)}$

# Rotation matrix
$T_{ij}(\varphi)$ is the identity matrix that has besides ones on the diagonal following elements:
$t_{ii} = \cos\varphi$,
$t_{ij} = -\sin\varphi$
$t_{ji} = \sin\varphi$
$t_{jj} = \cos\varphi$
This matrix corresponds to a rotation in $Ox_ix_j$ plane on angle $\varphi$
## Properties
1. This matrix is orthogonal.
2. $y = T_{ij}x \Leftrightarrow y_i = cx_i - sx_j \wedge y_j = sx_i + cx_j$. Everything else stays the same
3. Let $x \in \mathbb{R}^n, x \neq 0$. Then there is a sequence of rotation matrices that transforms $x$ to a basis vector: $T_{1n}\ldots T_{13}T_{12}x = \|x\|e^{(1)}$

Choose $\varphi$ such that
$\sin\varphi \cdot x_i + \cos\varphi \cdot x_j = 0 \Rightarrow \tan \varphi = - \frac{x_j}{x_i}$
Then
$x = x^{(0)} = {^t}(x_1 \ x_2 \ x_3 \ \ldots \ x_n), \ x^{(1)} = T_{12}x^{(0)} = {^t}(x_1 \ 0 \ x_3 \ \ldots \ x_n), \ x^{(2)} = T_{13}x^{(1)} = {^t}(x_1 \ 0 \ 0 \ \ldots \ x_n)$
$T_1 = T_{1n}\ldots T_{13}T_{12}$ and $T_1x = \|x\| e^{(1)}$
# The rotation method
Let $c_{12}$ and $s_{12}$ be some non-zero numbers and suppose we have a problem $Ax = b$.

Eliminate $x_1$ from second equation
$(c_{12}a_{11} + s_{12}a_{21})x_1 + \ldots + (c_{12}a_{1n} + s_{12}a_{2n})x_n = c_{12}b_1 + s_{12}b_2$
$(-s_{12}a_{11} + c_{12}a_{21})x_1 + \ldots + (-s_{12}a_{1n} + c_{12}a_{2n})x_n = -s_{12}b_1 + c_{12}b_2$

Conditions on $c_{12}$ and $s_{12}$:
$c_{12}^2+s_{12}^2 = 1$
$-s_{12}a_{11} + c_{12}a_{21} = 0$
Therefore
$c_{12} = \frac{a_{11}}{\sqrt{a_{11}^2+a_{21}^2}}, \ s_{12} = \frac{a_{21}}{\sqrt{a_{11}^2+a_{21}^2}}$
We just constructed $T_{12}$

Eliminate $x_2$ from third equation with $c_{13}$ and $s_{13}$:
$c_{13} = \frac{a_{11}^{(1)}}{\sqrt{(a_{11}^{(1)})^2+a_{31}^2}}, \ s_{13} = \frac{a_{31}}{\sqrt{(a_{11}^{(1)})^2+a_{31}^2}}$
After $n-1$ eliminations:
$a_{11}^{(n-1)}x_1 + a_{12}^{(n-1)}x_2 + \ldots + a_{1n}^{(n-1)}x_n = b_1^{(n-1)}$
$a_{22}^{(1)}x_2 + \ldots + a_{2n}^{(1)}x_n = b_2^{(1)}$
$\vdots$
$a_{n2}^{(1)}x_2 + \ldots + a_{nn}^{(1)}x_n = b_n^{(1)}$
In matrix form: $A^{(1)}x = b^{(1)}$, $A^{(1)} = T_{1n}\ldots T_{13}T_{12}A, \ b^{(1)} = T_{1n}\ldots T_{13}T_{12}b$

On the second step of the method we eliminate $x_2$ and we have:
$A^{(2)}x = b^{(2)}, \ A^{(2)} = T_{2n}\ldots T_{24}T_{23}A^{(1)}, \ b^{(2)} = T_{2n}\ldots T_{24}T_{23}b^{(1)}$

In the end we have:
$a_{11}^{(n-1)}x_1 + a_{12}^{(n-1)}x_2 + \ldots + a_{1n}^{(n-1)}x_n = b_1^{(n-1)}$
$a_{22}^{(n-1)}x_2 + a_{23}^{(n-1)}x_3 + \ldots + a_{2n}^{(n-1)} = b_2^{(n-1)}$
$\vdots$
$a_{nn}^{(n-1)}x_n = b_n^{(n-1)}$

In matrix form: $A^{(n-1)}x = b^{(n-1)}, \ A^{(n-1)} = T_{n-1,n}A^{(n-2)}, \ b^{(n-1)} = T_{n-1,n}b^{(n-2)}$

Matrix $A^{(n-1)}$ is upper triangular:
$A^{(n-1)} = TA, \ T = T_{n-1,n}\ldots T_{2n}\ldots T_{23}T_{1n} \ldots T_{12}$
$T$ is an orthogonal matrix $\Rightarrow$ we got a $QR$ decomposition of $A$
# Remainder of non-iterative processes
I got lazy, so reflection method and orthogonalization method will be written down in a notebook (but fully in English as usual)

# Iterative methods
**Formulation of a problem:**
Solve the problem $Ax = b$ in such way that $\|x^{(k)} - x^*\| < \varepsilon$

A sequence of vectors builds:
$\{x^{(k)}\}: \ x^{(0)} \in \mathbb{R}^n, \ x^{(k)} = \Phi_k(A, b, x^{(k-1)}, \ldots, x^{(k-r)})$
$\underset{k \to \infty}{\lim}x^{(k)} = x^*$

## Classification
1. $r = 1$ - one-step method, $r > 1$ - multistep method
2. $\Phi_k$ is a linear function of $x^{(i)} \Rightarrow$ method is called *linear*, else - *non-linear*
3. $\Phi_k$ is depends on $k \Rightarrow$ method is called *non-stationary*, else - *stationary*
## Linear one-step methods
**Canonical form**
$B_k \frac{x^{(k+1)} - x^{(k)}}{\alpha_k}+Ax^{(k)} = b$, where
$B_k$ and $\alpha_k$ are canonical parameters that generally depend on $k$

# The simple-iteration method
$Ax = b \Leftrightarrow x = Cx + g$                        (1)
$x^{(k+1)} = Cx^{(k)} + g, \ k = 0, 1,\ldots$         (2)

## The simple-iteration method convergence theorem (sufficient conditions)
If $\|C\| < 1$ then $\exists !$ solution of (1), sequence (2) converges to it $\forall x^{(0)} \in \mathbb{R}^n$ and following estimations are true:
$\|x^* - x^{(k)}\| \leq \frac{\|C\|}{1 - \|C\|}\|x^{(k)} - x^{(k-1)}\|$    (3)
$\|x^* - x^{(k)}\| \leq \frac{\|C\|^k}{1-\|C\|}\|x^{(1)} - x^{(0)}\|$        (4)

**Proof:**
(2) $\Rightarrow x^{(k+1)} - x^{(k)} = C(x^{(k)} - x^{(k-1)}) \Rightarrow \|x^{(k+1)} - x^{(k)}\| \leq \|C\| \|x^{(k)} - x^{(k-1)}\|$

$\|x^{(k+m)} - x^{(k)}\| \leq \|x^{(k+m)} - x^{(k+m-1)}\| + \ldots + \|x^{(k+2)} - x^{(k+1)} \| + \|x^{(k+1)} - x^{(k)}\| \leq$ 

$\|C\|^m\|x^{(k)} - x^{(k-1)}\| + \ldots + \|C\|^2 \|x^{(k)} - x^{(k-1)}\| + \|C\| \|x^{(k)} - x^{(k-1)}\| =$ 

$\frac{\|C\|(1-\|C\|^m)}{1-\|C\|}\|x^{(k)} - x^{(k-1)}\| \leq \frac{\|C\|^k}{1-\|C\|}(1-\|C\|^m)\|x^{(1)} - x^{(0)}\|$

Fix $m$ and $k \to \infty \Rightarrow$ $x^{(k)}$ is a fundamental sequence $\Rightarrow$ it has a limit $x^*$
$x^* = Cx^* +g$

Fix $k$ and $m \to \infty$:
$\|x^{(k+1)}  - x^{(k)} \| \leq \frac{\|C\|(1-\|C\|)^m}{1-\|C\|}\|x^{(k)}  - x^{(k-1)}\| \leq \frac{\|C\|^k(1-\|C\|^m)}{1-\|C\|}\|x^{(1)}-x^{(0)}\|$
$\square$

## Notes
1. (3) is being used to stop method: $\|x^{(k)} - x^{(k-1)}\| < \frac{1-\|C\|}{\|C\|}\varepsilon$
2. If $\|C\| < 1/2$ we can use $\|x^{(k)} - x^{(k-1)}\| < \varepsilon$

# How to rewrite the system for iterations?
$Ax = b \Leftrightarrow 0 = -\alpha(Ax-b), \ \alpha \neq 0 \Leftrightarrow Bx = Bx - \alpha(Ax-b), \det(B) \neq 0$

$x = x - \alpha B^{-1}(Ax-b) \Leftrightarrow x = Cx + \alpha B^{-1}b$, where $C = (E - \alpha B^{-1}A)$

**Canonic form of a method:**
$B\frac{x^{(k+1)} - x^{(k)}}{\alpha} + Ax^{(k)} = b$

1. $B = E$
$x^{(k+1)} = x^{(k)} - \alpha(Ax^{(k)} - b) = (E- \alpha A)x^{(k)} + \alpha b$
Let $A$ be a symmetrical positive definite matrix, $\lambda_{max}$ - its max eigenvalue
Condition $\|C\|_2 < 1$ will be satisfied if $\alpha \in (0, 2/\lambda_{max})$.

2. $\alpha = 1, \ B = diag(A) = D$
$x^{(k+1)} = x^{(k)} - D^{-1}(Ax^{(k)}-b) = (E-D^{-1}A)x^{(k)} + D^{-1}b$

If $D = D_A$ - we get Jacobi iterations
# Jacobi iterations
$C = \begin{bmatrix} 0 & -\frac{a_{12}}{a{11}} & -\frac{a_{13}}{a_{11}} & \cdots & -\frac{a_{1n}}{a_{11}} \\ -\frac{a_{21}}{a_{22}} & 0 & -\frac{a_{23}}{a_{22}} & \cdots & -\frac{a_{2n}}{a_{22}} \\ \cdots & \cdots & \cdots & \cdots & \cdots \\ -\frac{a_{n1}}{a_{nn}} & -\frac{a_{n2}}{a_{nn}} & -\frac{a_{n3}}{a_{nn}} & \cdots & 0 \end{bmatrix}$

If $\|C\| = \|C\|_{\infty}$, then sufficient condition of method's convergence is
$\|C\|_{\infty} = \underset{1 \leq i \leq n}{\max}\sum_{j = 1}^n |c_{ij}| < 1$,
which is equivalent to
$\sum_{j = 1, \ j \neq i}^n |a_{ij}| < |a_{ii}|, \ i = 1, \ldots, n$

# Necessary and sufficient conditions of simple iterations method convergence
## Lemma
If all eigenvalues $|\lambda_C| < 1$ then $\sum_{i = 0}^{\infty}C^k = (E-C)^{-1}$
**Proof:**
$S_k = E + C + \ldots + C^k$
$S_k(E-C) = E - C + C - C^2 + \ldots + C^k - C^{k-1} = E - C^{k-1}$ (\*)
$\forall \lambda: \ |\lambda_C| < 1 \Leftrightarrow \underset{k \to \infty}{\lim}C^{k+1} = 0 \Rightarrow$ left side of (\*) has a limit $\Rightarrow S_k$ has a limit.
Suppose $\underset{k \to \infty}{\lim}S_k = S \Rightarrow S(E-C) = E \Rightarrow S = (E-C)^{-1}$
$\square$
## Theorem
Sequence $x^{(k+1)} = Cx^{(k)} + g$ converges $\Leftrightarrow \forall \lambda_C: |\lambda_C| < 1$
**Proof:**
$\Rightarrow$
Suppose $x^* = \underset{k \to \infty}{\lim}x^{(k)}$
$x^{(k)} - x^* = C(x^{(k-1)} - x^*) = C^2(x^{(k-2)} - x^*) = \ldots = C^k(x^{(0)} - x^*)$ (\*\*)
$x^{(0)}$ is any vector. Let $x^{(0)} - x^* = e^{(p)}$. Then in right side of (\*\*) the p-th column of $C^k$ remains and approaches zero $\Rightarrow C^k \underset{k \to \infty}{\longrightarrow} 0 \Leftrightarrow \forall \lambda_C: \ |\lambda_C| < 1$

$\Leftarrow$
$x^{(k)} = Cx^{(k-1)} + g = C(Cx^{(k-2)} + g) + g = C^2x^{(k-2)} + (E + C)g =$
$= C^kx^{(0)} + (E + C + \ldots + C^k)g \underset{k \to \infty}{\longrightarrow} (E - C)^{-1}g$
$\square$

# Gauss-Seidel iterations
This method is basically the simple-iteration method, but while computing components of $(k+1)$-th vector substitute components of $k$-th vector with already computed components of $(k+1)$-th vector.

# Seidel iterations
$C = \underline{C} + \bar{\bar{C}}$
$\underline{C} = \begin{bmatrix} 0 & 0 & \cdots & 0 & 0 \\ c_{21} & 0 & \cdots & 0 & 0 \\ \cdots & \cdots & \cdots & \cdots & \cdots \\ c_{n1} & c_{n2} & \cdots & c_{n, n-1} & 0 \end{bmatrix}, \ \bar{\bar{C}} = \begin{bmatrix} c_{11} & c_{12} & \cdots & c_{1, n-1} & c_{1, n} \\ 0 & c_{22} & \cdots & c_{2, n-1} & c_{2, n} \\ \cdots & \cdots & \cdots & \cdots & \cdots \\ 0 & 0 & \cdots & 0 & c_{nn} \end{bmatrix}$

$x^{(k+1)} = \underline{C}x^{(k+1)} + \bar{\bar{C}}x^{(k)} + g$

$(E - \underline{C})x^{(k+1)} = \bar{\bar{C}}x^{(k)} + g$
$\det(E- \underline{C}) = 1 \Rightarrow \exists (E - \underline{C})^{-1}$

$x^{(k+1)} = (E - \underline{C})^{-1}\bar{\bar{C}}x^{(k)} + (E - \underline{C})^{-1}g = Bx^{(k)} + f$

## Sufficient conditions of Seidel method convergence
$\|C\|_{1,2,\infty} < 1 \Rightarrow$ method converges.

**Proof** (only for infinite norm):

