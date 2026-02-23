# sensitivity analysis

linear approx of $t = \epsilon$ would be $f_1(\epsilon) = f(0) + f'(0) \epsilon$
then want to extend approx to $t = 2\epsilon$

---

first method is iterating linear approxs
i.e. assuming that $b$ and $m$ values also need to be approxed

using $f_1(2 \epsilon) = f(\epsilon) + f'(\epsilon) \epsilon$
$f(\epsilon)$ can be derived from $f(0) + f'(0) \epsilon$
$f'(\epsilon)$ can be linear approxed itself as $f'(0) + f''(0) \epsilon$

substituting, $f_1(2 \epsilon) = f(0) + f'(0) \epsilon + (f'(0) + f''(0) \epsilon) \epsilon$
which gives $f_1(2 \epsilon) = f(0) + 2f'(0) \epsilon + f''(0) \epsilon^2$

---

second method is by using quadratic approx directly

from taylor, $f_2(x) = f(0) + f'(0) x + \frac{f''(0)}{2!} x^2$
applying, $f_2(2 \epsilon) = f(0) + 2f'(0)\epsilon + 2f''(0)\epsilon^2$

---

[desmos graph](https://www.desmos.com/calculator/gz4kvmv36b)

## writeup

Approximations in general can be defined as trying to fit some function $f(x)$ with some simpler function $g(x)$. There are many reasons to do this—for example, one is that $f(x)$ may not be represented by a simple equation and rather is an arbitrary curve, which means that the $g(x)$ approximation could simplify the function into a rational function. If $f(x)$ is already a polynomial, finding $g(x)$ becomes pretty easy since it can just be a function of the same degree. However, the main difficulty comes when fitting to non-polynomial functions, which requires more complicated $g(x)$ approximations.

In this scenario, we work with two different types of approximations. The first is linear approximations, which use the equation for a line: $y = mx + b$. For this $g(x)$, $m$ and $b$ are the unknowns, which need to be found in relation to the $f(x)$ function trying to be fit to. In this case, we can use $f(0)$ and $f'(0)$, which are the intercept at $0$ and slope at $0$ respectively (which are literally what $b$ and $m$ are). So, we get $g(x) = f(0) + f'(0)x$.

The other approximation type is using the Taylor series. Of the form $g(x) = f(a) + f'(a)(x - a) + \frac{f''(a)}{2!}(x - a)^2 + \dots + \frac{f^{(n)}}{n!}(x - a)^n$, the series is used for approximating functions up to a certain point of complexity (usually seen as changes in direction in $f(x)$). The series is taken as a given in this case, but it can be proved through integrals.

Now, for the actual problem. At $f(\epsilon)$, we can use a linear approximation; but, when we're trying to extend the approximation to $f(2 \epsilon)$, a quadratic term is desired to cap the approximation's error. Two methods can be used in this case: iterating linear approximations or using a proper Taylor series approximation.

### Iterating linear approximations

For iterating linear approximations, we use the form $f_1(2 \epsilon) = f(\epsilon) + f'(\epsilon) \epsilon$. This is because we can assume that the value at $2 \epsilon$ can be found by starting at the value at $\epsilon$ and following the slope at that point for the next $\epsilon$—i.e. $m\epsilon$. The unknowns in this case—which are values based on $f$ at $\epsilon$—can be found through their own set of linear approximations.

We know the values of $f$ at $0$, so using that, setting up approximations for the $b$ and $m$ at $\epsilon$,
$f(\epsilon) = f(0) + f'(0) \epsilon$
$f'(\epsilon) = f'(0) + f''(0) \epsilon$

Now, substituting into our original equation,
$f_1(2 \epsilon) = f(0) + f'(0) \epsilon + (f'(0) + f''(0) \epsilon) \epsilon$

And simplifying, we finally get,
$f_1(2 \epsilon) = f(0) + 2f'(0) \epsilon + f''(0) \epsilon^2$

## Taylor polynomial

This method is a lot simpler.

We just take terms from the Taylor series until we create a quadratic,
$f_2(x) = f(a) + f'(a)(x - a) + \frac{f''(a)}{2!}(x - a)^2$

Using $a = 0$ since we're working with $f$ at $0$, after applying our form we get,
$f_2(2 \epsilon) = f(0) + 2f'(0) \epsilon + 2f''(0) \epsilon^2$

### Comparison

Putting the approximations side-by-side, they look pretty similar:
$f_1(2 \epsilon) = f(0) + 2f'(0) \epsilon + f''(0) \epsilon^2$ (linear iterations)
$f_2(2 \epsilon) = f(0) + 2f'(0) \epsilon + 2f''(0) \epsilon^2$ (Taylor polynomial)

The main difference in form is the $2$ factor on the $\epsilon^2$ term. The actual difference in outcome comes from the problem with linear iterations: the slope is only approximated for the $[0, \epsilon]$ section and assumed to be held constant, which means changes that happen later are completely missed. Thus, the Taylor polynomial approach gives an overall better approximation.
