# sensitivity analysis

linear approx of $t = \epsilon$ would be $f_1(\epsilon) = f(0) + f'(0) \epsilon$
then want to extend approx to $t = 2\epsilon$

---

first method is iterating linear approxs
i.e. assuming that $b$ and $m$ values also need to be approxed

using $f_1(2 \epsilon) = f(\epsilon) + f'(\epsilon) \epsilon$
$f(\epsilon)$ can be derived from $f_1(\epsilon) = f(0) + f'(0) \epsilon$
$f'(\epsilon)$ can be linear approxed itself as $f'(\epsilon) = f'(0) + f''(0) \epsilon$

substituting, $f_1(2 \epsilon) = f(0) + f'(0) \epsilon + (f'(0) + f''(0) \epsilon) \epsilon$
which gives $f_1(2 \epsilon) = f(0) + 2f'(0) \epsilon + f''(0) \epsilon^2$

---

second method is by using quadratic approx directly

from taylor, $f_2(x) = f(0) + f'(0) x + \frac{f''(0)}{2!} x^2$
simplifying, $f_2(2 \epsilon) = f(0) + 2f'(0)\epsilon + 2f''(0)\epsilon^2$

---

[desmos graph](https://www.desmos.com/calculator/gz4kvmv36b)

## questions

> why are the two approximations different?

iterating linear approximations gives an equation based on approximating $b$ and then approximating $m$, with the latter multiplied by the moved $2 \epsilon$. since the approximations are based on the change of $0 \rightarrow \epsilon$, the function only approximates the slope for that section but attempts to apply it to $2 \epsilon$. for the second method, a quadratic equation is properly formed based on the taylor series, which uses actual derivative values from $f$.

> which is a better approximation?

the second one, since it properly takes the quadratic curve into account by using a properly formed equation based on the taylor series.

> does this difference persist as we iterate linear approximations farther from the base of $t = 0$

yes, and it gets worse as the function moves away from $t = 0$ since the iterative linear approximation will get continually worse as it is unable to fully take into account the non-linear quadratic term of $\epsilon^2$.
