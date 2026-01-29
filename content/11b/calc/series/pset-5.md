# problem set 5

## 1

$a_0 = 1, a_1 = -\frac{1}{\sqrt{3}}, a_2 = \frac{1}{3}, a_3 = -\frac{1}{3 \sqrt{3}}$

$b_n = \sum^n_{k = 1} a_k$
$B = \lim_{n \rightarrow \infty} b_n$
$|b_n - B| < \epsilon$, i.e. sum from $n$ to $\infty$

$b_n = \sum^n_{k = 1} (-\frac{1}{\sqrt{3}})^k$
$r = -\frac{1}{\sqrt{3}}$, sum is $\frac{1 - r^n}{1 - r}$
$n = \infty$, sum is $\frac{1}{1 - r}$

$|b_n - B| < \epsilon$
$|\frac{1 - r^n}{1 - r} - \frac{1}{1 - r}| < \epsilon$
$|-r^n| < \epsilon \cdot (1 - r)$
solve for $n$ for $M$?

## 7

$\sum^\infty_{n = 1} \frac{\sqrt{n + 1} - \sqrt{n - 1}}{2}$

$\frac{\sqrt{2} - \sqrt{1}}{2}, \frac{\sqrt{3} - \sqrt{2}}{2}, \frac{\sqrt{4} - \sqrt{3}}{2}, \frac{\sqrt{5} - \sqrt{4}}{2}$
$0.207, 0.366, 0.5, 0.618$

$\frac{1}{2}(\sum^\infty_{n = 1} \sqrt{n + 1} - \sum^\infty_{n = 1} \sqrt{n - 1})$
...
