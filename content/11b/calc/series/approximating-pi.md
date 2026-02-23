# approximating $\pi$

$\frac{\pi}{4} = 4tan^{-1}(\frac{1}{5}) - tan^{-1}(\frac{1}{x})$
$tan^{-1}(\frac{1}{x}) = -\frac{\pi}{4} + 4tan^{-1}(\frac{1}{5})$
$\frac{1}{x} = tan(-\frac{\pi}{4} + 4tan^{-1}(\frac{1}{5}))$
$x = 239$

$\frac{\pi}{4} = 4tan^{-1}(\frac{1}{5}) - tan^{-1}(\frac{1}{239})$
$\pi = 16tan^{-1}(\frac{1}{5}) - 4tan^{-1}(\frac{1}{239})$

$f(a) + f'(a) (x - a) + \frac{f''(a)}{2!} (x - a)^2 + \dots + \frac{f^n(a)}{n!} (x - a)^n$
$g(x) = x - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \dots + (-1)^n \frac{x^{2n + 1}}{2n + 1}$

$\pi = 16g(\frac{1}{5}) - 4g(\frac{1}{239})$
err of $g$ needs to be $< 5 \times 10^{-7}$ for proper 6 places

for some $n$ terms, error bound is $|tan^{-1}(x) - g_n(x)| \le |\frac{x^{2(n + 1) + 1}}{2(n + 1) + 1}|$, since next term is omitted and term values are decreasing because $|x| < 1$

need $\sum k \times |\frac{x^{2(n + 1) + 1}}{2(n + 1) + 1}| < 5 \times 10^{-7}$ for $k = 16, x = \frac{1}{5}$ and $k = 4, x = \frac{1}{239}$
$16|\frac{\frac{1}{5}^{2(n + 1) + 1}}{2(n + 1) + 1}| + 4|\frac{\frac{1}{239}^{2(n + 1) + 1}}{2(n + 1) + 1}| < 5 \times 10^{-7}$

solving, $n = 3.1743$
so choose terms up to $k = 4$, $g(x) = x - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \frac{x^9}{9}$
