# optimizing unimodal functions

## ternary search

```cpp
template <typename F> int find_min(int l, int r, const F &f) {
    while (r - l > 3) {
        int m1 = l + ((r - l) / 3);
        int m2 = r - ((r - l) / 3);
        f(m1) > f(m2) ? l = m1 : r = m2;
    }

    int res = l;
    for (int i = l + 1; i <= r; i++) {
        if (f(i) < f(res)) res = i;
    }
    return res;
}
```

## haybale distribution

* compute prefix sums for $x$, define $range(l, r) = pref[r + 1] - pref[l]$
* total wasted is $\sum (a * (y - x_i)) \text{ } \forall x_i < y + \sum(b * (x_i - y)) \text{ } \forall x_i \geq y$
* where $k$ is the index of $y$, thus the count of $x_i < y$
    * left side is $a * (y * k - range(0, k - 1))$
        * $a * \sum(y - x_i) = a * \sum y - \sum x_i = \dots$
    * right side is $b * (range(k, n - 1) - y * (n - k))$
    * $cost(k) = left(k) + right(k)$, and $y$ is $x_k$
* find inflection point of $cost(k)$ using a search, minimum is solution
* (technically there is duplicate handling but not in scope)
