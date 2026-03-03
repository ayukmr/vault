# problems

## pset #2

1)

$f(x) = (2 - x)(x + 1)$
from $x = -2$ to $x = 2$

$A \approx L_n = f(x_0) \Delta x + f(x_1) \Delta x + \dots + f(x_n - 1) \Delta x = \sum^n_{i = 1} f(x_{i - 1})\Delta x$

$L = f(-2)0.5 + f(-1.5)0.5 + f(-1)0.5 + f(-0.5)0.5 + f(0)0.5 + f(0.5)0.5 + f(1)0.5 + f(1.5)0.5$
$R = f(-1.5)0.5 + f(-1)0.5 + f(-0.5)0.5 + f(0)0.5 + f(0.5)0.5 + f(1)0.5 + f(1.5)0.5 + f(2)0.5$

$L = 1.5, R = 3.5$

2)

$\lim_{n \rightarrow \infty} \sum^n_{i = 1} f(a + \frac{(i - 1)(b - a)}{n}) \cdot \frac{(b - a)}{n}$

$L = \lim_{n \rightarrow \infty} \sum^n_{i = 1} f(-2 + \frac{4(i - 1)}{n}) \cdot \frac{4}{n}$
$R = \lim_{n \rightarrow \infty} \sum^n_{i = 1} f(-2 + \frac{4i}{n}) \cdot \frac{4}{n}$

$L = R$
$\lim_{n \rightarrow \infty} \sum^n_{i = 1} f(-2 + \frac{4(i - 1)}{n}) \cdot \frac{4}{n} = \lim_{n \rightarrow \infty} \sum^n_{i = 1} f(-2 + \frac{4i}{n}) \cdot \frac{4}{n}$

$L - R = \lim_{n \rightarrow \infty} [\frac{4}{n} \cdot \sum^n_{i = 1} [f(-2 + \frac{4(i - 1)}{n}) - f(-2 + \frac{4i}{n})]]$ 
cancels. as $\sum^n_{i = 1} f(x_{i - 1}) - f(x_i) = f(0) - f(n)$,
so $\sum^n_{i = 1} [f(-2 + \frac{4(i - 1)}{n}) - f(-2 + \frac{4i}{n})] = f(-2) - f(-2 + 4)$
and $L - R = \lim_{n \rightarrow \infty} \frac{4}{n} \cdot (f(-2) - f(-2 + 4))$

when taking the limit, $\frac{4}{n} \cdot (f(-2) - f(-2 + 4)) = 0$
so $L = R$, since $L - R = 0$

3)

range is from $-2$ to $2$, meaning range is $4$
using $\Delta x > 4$ means 'width' will exceed range
so $0 < \Delta x \le 4$ for having true area bounded between $L$ and $R$
