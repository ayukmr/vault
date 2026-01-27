# power series

$$\sum^{\infty}_{n = 0}{c_n (x - a)^n} = c_0 + c_1(x - a) + c_2(x - a)^2 + \dots$$

1. series converges for all $x = a$, diverges for all $x \ne a$
2. series converges for all real numbers $x$
3. exists a real number $R > 0$ s.t. converges if $|x - a| < R$ and diverges if $|x - a| > R$. at $|x - a| = R$, may converge or diverge

---

if there exists a real number $d \ne 0$ such that $\sum^{\infty}_{n = 0}{c_n d^n}$ converges, then the series $\sum^{\infty}_{n = 0}{c_n x^n}$ converges absolutely for all $x$ such that $|x| < |d|$

since $\sum^{\infty}_{n = 0}{c_n d^n}$ converges, the $n$th term $c_nd^n \rightarrow 0$ as $n \rightarrow \infty$
therefore, exists an integer $N$ such that $|c_n d^n| \le 1$ for all $n \ge N$

turning $d$ into $x$, $|c_n x^n| = |c_n d^n| |\frac{x}{d}|^n$

and since limiting $n$ to having $|c_n d^n| \le 1$
$|c_n x^n| \le |c_n d^n| \cdot |\frac{x}{d}|^n \le 1 \cdot |\frac{x}{d}|^n$ holds
so $|c_n x^n| \le |\frac{x}{d}|^n$

the series $\sum^{\infty}_{n = N}{|c_n x^n|} \le \sum^{\infty}_{n = N}{|\frac{x}{d}|^n}$ converges if $|\frac{x}{d}| \le 1$, which it is
so $\sum^{\infty}_{n = N}{|c_n x^n|}$ must converge based on being squeezed by $\le$

---

$f(x) = \frac{x^3}{2 - x}$ into power series

$\frac{x^3}{2 - x} = c_0 + c_1 x + c_2 x^2 + c_3 x^3 + c_4 x^4 + \dots$

moving $2 - x$ to right
multiplying $2 - x$ by each term gives $2 c_n x^n$ and $-c_n x^{n + 1}$
rearranging, $\frac{x^3}{2 - x} = 2c_0 + (2c_1 - c_0)x + (2c_2 - c_1)x^2 + (2c_3 - c_2)x^3 + \dots$

removing terms, so $c_{0 .. 2} = 0$
but need $x^3$ term, so $c_3 = \frac{1}{2}$ (as $2c_3 = 1$)
in $x^4$ term, need to get rid of $-c_3$ now, so $c_4 = \frac{1}{4}$ (as $2c_4 = c_3 = \frac{1}{2}$)
in $x^5$ term, need to get rid of $c_4$ and so on...

$c_{0..2} = 0$
$c_{n \ge 3} = \frac{1}{2^{n - 2}}$

$\frac{x^3}{2 - x} = \sum^{\infty}_{k = 3}{\frac{1}{2^{k - 2}} x^k} = 4\sum^{\infty}_{k = 3}{(\frac{x}{2})^k}$

converges at $|\frac{x}{2}| < 1$, $|x| < 2$
interval of convergence is $(-2, 2)$
