---
title: Meet in the Middle
tags:
  - algorithms
---

* Technique where search space is divided in two
* Search is performed for each part and results are combined
* With list of numbers $n$ and finding sum of numbers $x$
    * Divide list $n$ into two half lists $A$ and $B$
    * Generate subsets for both lists as $S_A$ and $S_B$
    * Choose elements from each and check if equals $x$

```python
from itertools import combinations, product, chain

def subsets(ary):
    return list(
        chain.from_iterable([
            [sum(j) for j in combinations(ary, i)]
            for i in range(1, len(ary) + 1)
        ])
    )

n = [1, 2, 3, 4, 5]
x = 9

h = int(len(n) / 2)

a = n[:h]
b = n[h:]

s_a = subsets(a)
s_b = subsets(b)

possible = any(i + j == x for i, j in product(s_a, s_b))
print(possible)
```
