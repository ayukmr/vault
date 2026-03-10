# oscillating integers

working with $f(x) = sin(\frac{\pi}{x})$ on interval $[0, 1]$
as $x$ approaches $0$, function oscillates with ever-increasing frequency

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

---

basic riemann sum form is $\sum^n_{i = 1} f(a + \frac{(i - 1)(b - a)}{n}) \cdot \frac{(b - a)}{n}$
but actually, use rectangles at middle, so $\sum^n_{i = 1} f(a + \frac{(i - 0.5)(b - a)}{n}) \cdot \frac{(b - a)}{n}$

main problem is that whatever $\Delta x$ is chosen, it'll be too big for the increasingly small curves when going $\rightarrow 0$
i.e., need to scale $n$ somehow

instead of having $a = 0$ and $b = 1$, take some $a = \frac{1}{n + 1}$ and $b = \frac{1}{n}$
so now have some $g(a, b) = \sum^n_{i = 1} f(a + \frac{(i - 0.5)(b - a)}{n}) \cdot \frac{(b - a)}{n}$

and then for each section, want to have some $k$ bars, so $n = k$
so each has a $\Delta x = \frac{(b - a)}{k}$

and then have the actual function like $h(n) = \sum^n_{i = 1} g(\frac{1}{i + 1}, \frac{1}{i})$

trying to graph this out in desmos, first need to compute the position of $i$, say using function $i_x$

taking in endpoints, $i_x(a, b, x)$. trying to normalize $x$ from $[a, b]$ to $[1, k]$,
so $x - a$, $\frac{x - a}{b - a}$, $\frac{k(x - a)}{b - a}$, $i_x(a, b, x) = \frac{k(x - a)}{b - a} + 1$
and since discrete, need to get nearest $i$, so $i_x(a, b, x) = \lfloor \frac{k(x - a)}{b - a} \rfloor$

the computation for a given rectangle height is the same—using some $x(a, b, i) = a + \frac{(i - 0.5)(b - a)}{k}$
combining, over range $[a, b]$, use $x(a, b, i_x(a, b, x))$ to get $x$s

so now, in desmos, represent this as $r_x(a, b, x) = \{ a \le x \le b: x(a, b, i_x(a, b, x)) \}$
and want to put these x values into $f$, so $f(r_x(a, b, x))$

and highlight above and below axes with $\le y \le 0$ or $0 \le y \le$

---

$S = \int_0^1 sin(\frac{\pi}{x}) dx$
$R = \int_0^1 |sin(\frac{\pi}{x})| dx$
$T = \int_0^1 sin^2(\frac{\pi}{x}) dx$

$0 < |y| < 1$ implies $0 \le y^2 \le |y|$
excluding $0$ and $1$, working with $0 < |sin(\frac{\pi}{x})| < 1$, so $0 < sin^2(\frac{\pi}{x}) < |sin(\frac{\pi}{x})|$
and since not all $sin(\frac{\pi}{x}) = 0, 1$ on a set of $x$s, strictly $sin^2(\frac{\pi}{x}) < |sin(\frac{\pi}{x})|$
and thus, $T < R$, and by extent, $0 < T < R$

with $-S < T$, turns into $S + T > 0$
so $\int_0^1 [sin(\frac{\pi}{x}) + sin^2(\frac{\pi}{x})]dx > 0$

splitting at zeros, $I_n = \int_{1/(n + 1)}^{1/n} [sin(\frac{\pi}{x}) + sin^2(\frac{\pi}{x})]dx$
pairing $\frac{1}{n}$ to $\frac{1}{n + 1}$, gives $x$ -> $\frac{x}{1 + x}$

over a cycle, $sin(\frac{\pi}{x})$ changes sign, $sin^2(\frac{\pi}{x})$ stays the same, $dx$ is divided by $(1 + x)^2$, but same otherwise
so $I_{n + 1} = \int_{1/(n + 1)}^{1/n} [-sin(\frac{\pi}{x}) + sin^2(\frac{\pi}{x})] \frac{dx}{(1 + x)^2}$
as one, $I_n + I_{n + 1} = \int_{1/(n + 1)}^{1/n} [sin(\frac{\pi}{x}) + sin^2(\frac{\pi}{x})]dx + \int_{1/(n + 1)}^{1/n} [-sin(\frac{\pi}{x}) + sin^2(\frac{\pi}{x})] \frac{dx}{(1 + x)^2}$
and combining, $I_n + I_{n + 1} = \int_{1/(n + 1)}^{1/n} [sin(\frac{\pi}{x}) + sin^2(\frac{\pi}{x}) \frac{-sin(\frac{\pi}{x}) + sin^2(\frac{\pi}{x})}{(1 + x)^2}]dx$
and factoring, $I_n + I_{n + 1} = \int_{1/(n + 1)}^{1/n} [sin(\frac{\pi}{x})(1 - \frac{1}{(1 + x)^2}) + sin^2(\frac{\pi}{x})(1 + \frac{1}{(1 + x)^2})]dx$

when choosing $n$ s.t. $sin(\frac{\pi}{x}) \ge 0$, then also $sin^2(\frac{\pi}{x}) > 0$ (as always)
and more importantly $1 + \frac{1}{(1 + x)^2},  1 - \frac{1}{(1 + x)^2} > 0$
so everything is positive and $I_n + I_{n + 1} > 0$
so $-S < T$

already know $-R < S < 0$
now know $-S < T < R$
together, $0 < -S < T < R$
