---
title: Knapsack Algorithm
tags:
  - algorithms
---

```python
from collections import defaultdict

n = 5
s = 12

vs = [6, 10, 4, 11, 20]
ws = [1, 2, 3, 4, 5]

cs = defaultdict(lambda: defaultdict(lambda: -1))

def dp(i, r):
    if i == n or r == 0:
        return 0

    w = ws[i]
    v = vs[i]

    if w > r:
        cs[i][r] = dp(i + 1, r)
        return cs[i][r]

    c = cs[i][r]

    if c != -1:
        return c

    c = max(
        dp(i + 1, r - w) + v,
        dp(i + 1, r)
    )

    cs[i][r] = c
    return c

print(dp(0, s))
```
