---
title: Dijkstra's Algorithm
tags:
  - algorithms
---

* Finds shortest distances between source and other nodes in $O(n^2)$
* $d[v]$ for each $v$ with length of shortest path from $s$ to $v$
    * Initially, $d[s]$ is 0, other vertices have length of infinity
* Boolean array $u[v]$ for each $v$ which stores if $v$ is marked
* At each iteration, unmarked $v$ with lowest $d[v]$ is picked
    * In first iteration, starting $s$ is selected
    * Selected vertex $v$ is marked in $u[v]$
    * From $v$, relaxations are performed to reduce distance
        * For each edge of form $(v, to)$, algorithm tries to improve $d[to]$
        * If length of current edge is $len$, relaxation is $d[to] = min(d[to], d[v] + len)$
    * After $n$ iterations, all vertices will be marked
* Values are the shortest paths, infinite values are unreachable

```python
import math

# nodes
nodes = [
    [(1, 5), (2, 10), (5, 15)],
    [(5, 5)],
    [(3, 2)],
    [], [], [],
]
n = len(nodes)

# distances
d = [math.inf if i != 0 else 0 for i in range(n)]

# markings
u = [False for _ in range(n)]

# parents
p = [-1 for _ in range(n)]

for _ in range(n):
    v = None

    # find lowest v which is unmarked
    for i, vd in enumerate(d):
        if not u[i] and (v == None or vd < d[v]):
            v = i

    u[v] = True

    # iterate over edges
    for edge in nodes[v]:
        to = edge[0]
        length = edge[1]

        # set new distance if lower
        if d[v] + length < d[to]:
            d[to] = d[v] + length
            p[to] = v

print(d)
print(p)
```
