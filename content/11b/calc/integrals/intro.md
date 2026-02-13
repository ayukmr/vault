# riemann sums

$A \approx L_n = f(x_0) \Delta x + f(x_1) \Delta x + \dots + f(x_n - 1) \Delta x = \sum^n_{i = 1} f(x_{i - 1})\Delta x$

$\int_a^b f(x) dx$

$\lim_{n \rightarrow \infty} \sum^n_{i = 1} f(a + \frac{(i - 1)(b - a)}{n}) \cdot \frac{(b - a)}{n}$
height: $f(a + \frac{(i - 1)(b - a)}{n})$
width: $\frac{(b - a)}{n}$

$R_n$ is $L_n$ but starting at $i$ instead of $i - 1$

$\int_a^b [f(x) + g(x)] = \int_a^b f(x) + \int_a^b g(x)$
$\int_a^b c f(x) = c \int_a^b f(x)$
$\int_a^b f(x) = \int_a^c f(x) + \int_c^b f(x)$

average value: $f_{avg} = \frac{1}{b - a} \int_a^b f(x)$
