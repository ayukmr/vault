# oscillating integers

$f(x) = sin(\frac{\pi}{x})$ on interval $[0, 1]$

---

$S = \int_0^1 sin(\frac{\pi}{x})dx$
$R = \int_0^1 |sin(\frac{\pi}{x})|dx$

$\int_0^1 sin(\frac{\pi}{x})dx \le \int_0^1 |sin(\frac{\pi}{x})|dx$ by definition
which gives $-R < S$

zeros happen at $x = \frac{1}{n}$, for $n = 1, 2, 3, \dots$
for each interval $(\frac{1}{n + 1}, \frac{1}{n})$, area has sign $(-1)^n$
sum is essentially $S = \sum^{\infty}_{n = 1} \int_{1/(n + 1)}^{1/n} sin(\frac{\pi}{x}) dx$
and first interval is largest, which in this case is $(\frac{1}{2}, 1)$
which has sign of $(-1)^1 = -1$
all contributions are smaller in magnitude and alternate; so $S < 0$

together, $-R < S < 0$
