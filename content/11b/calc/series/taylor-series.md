# taylor series

$f(a) + f'(a) (x - a) + \frac{f''(a)}{2!} (x - a)^2 + \dots + \frac{f^n(a)}{n!} (x - a)^n$

## problems

first, second taylors for $\sqrt{x}$ at $x = 4$

$f(x) = \sqrt{a} + \frac{1}{2} a^{-\frac{1}{2}} (x - a) - \frac{\frac{1}{4} a^{-\frac{3}{2}}}{2} (x - a)^2$
$f(x) = 2 + 0.25 (x - 4) - 0.015625 (x - 4)^2$
$f(6) = 2.437$, $\sqrt{6} = 2.449$

$err \le \frac{max(|f^{(n + 1)}(x)|)}{(n + 1)!} |x - a|^{(n + 1)}$
$|\frac{3}{8} x^{-\frac{5}{2}}|$  @ $x = 4$ (for max deriv) $\rightarrow 0.0117$
$\frac{0.0117}{6} \cdot 2^3 = 0.0156$

fourth maclaurin polynomial for $cos(x)$

$f(x) = cos(0) + sin(0) x - \frac{cos(0)}{2!} x^2 - \frac{sin(0)}{3!} x^3 + \frac{cos(0)}{4!} x^4$
$f(\frac{\pi}{12}) = 0.965$, $cos(\frac{\pi}{12}) = 0.965$
