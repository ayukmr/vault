# series problems

## problem set 5

### 1

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

### 7

$\sum^\infty_{n = 1} \frac{\sqrt{n + 1} - \sqrt{n - 1}}{2}$

$\frac{\sqrt{2} - \sqrt{0}}{2}, \frac{\sqrt{3} - \sqrt{1}}{2}, \frac{\sqrt{4} - \sqrt{2}}{2}, \frac{\sqrt{5} - \sqrt{3}}{2}$
partials: $0.707, 1.073, 1.366, 1.618$

$\frac{1}{2}(\sum^\infty_{n = 1} \sqrt{n + 1} - \sqrt{n - 1})$
$\frac{1}{2}[(\sqrt{2} - \sqrt{0}) + (\sqrt{3} - \sqrt{1}) + (\sqrt{4} - \sqrt{2}) + (\sqrt{5} - \sqrt{3})]$
$\frac{1}{2}[(\sqrt{2} - \sqrt{2}) + (\sqrt{3} - \sqrt{3}) - \sqrt{0} - \sqrt{1} + \sqrt{4} + \sqrt{5}]$

so $-\sqrt{1}$ (i.e. $1$), $\sqrt{4}$, $\sqrt{5}$ don't cancel
$\sqrt{4}$ and $\sqrt{5}$ generalize to $\sqrt{N}$ and $\sqrt{N + 1}$
so $S = lim_{n \rightarrow \infty} [-1 + \sqrt{n} + \sqrt{n + 1}] \times \frac{1}{2}$
$S = lim_{n \rightarrow \infty}[\sqrt{n} + \sqrt{n + 1}]  \times \frac{1}{2} = \infty$

## slides

$\sum^\infty_{n = 3} \frac{(-1)^n n}{(n + 1)(2 - n)}$
$(-1)^n \cdot \frac{n}{(n + 1)(2 - n)}$

$\lim_{n \rightarrow \infty} \frac{n}{n + 2 - n^2}$
$\lim_{n \rightarrow \infty} \frac{n}{n + 2 - n^2} \cdot \frac{\frac{1}{n^2}}{\frac{1}{n^2}}$
$\lim_{n \rightarrow \infty} \frac{\frac{1}{n}}{\frac{1}{n} + \frac{2}{n^2} - 1}$
$\frac{0}{0 + 0 - 1} = \frac{0}{-1} = 0$
converges at $0$ at $\infty$

$b_n > b_{n + 1} > 0$
$\frac{n}{n + 2 - n^2} > \frac{n + 1}{n + 1 + 2 - (n + 1)^2}$
$\frac{n + 1}{n + 1 + 2 - (n + 1)^2} = \frac{n + 1}{n + 3 - n^2 - 1 - 2n} = \frac{n + 1}{-n + 2 -n^2}$
$\frac{n}{n + 2 - n^2} > \frac{n + 1}{-n + 2 - n^2}$, inequality holds
