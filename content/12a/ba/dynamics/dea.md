# data envelopment analysis

for this problem, I decided to write some code to run the many linear programs for the different facilities. converting it from the written out equations to a linear program was pretty straightforward, just converting a $\geq$ to a sign flipped $\leq$, and equality into two constraints.

```python
linprog(
    [0, 0, -1 * c[i], -1 * d[i]],
    [
        # -- efficiency within 100%
        # E = (c_i y_1 + d_i y_1) / (a_i x_1 + b_i x_2)
        # E <= 1
        # c_i y_1 + d_i y_1 <= a_i x_1 + b_i x_2
        # -a_i x_1 -b_i x_2 + c_i y_1 + d_i y_1 <= 0
        [-1 * a[k], -1 * b[k], 1 * c[k], 1 * d[k]]
        for k in range(n)
    ] + [
        # -- fixed denominator
        # a_i x_1 + b_i x_2 = 1
        [ 1 * a[i],  1 * b[i], 0, 0],
        [-1 * a[i], -1 * b[i], 0, 0],

        # -- non-negative prices
        # x_1, x_2, y_1, y_2 >= 0
        [-1,  0,  0,  0],
        [0,  -1,  0,  0],
        [0,   0, -1,  0],
        [0,   0,  0, -1],
    ],
    [0 for _ in range(n)] + [1, -1, 0, 0, 0, 0],
    bounds=[(None, None), (None, None), (None, None), (None, None)],
)
```

this runs for the $i$th facility. to figure out how many are relatively optimal, I calculated $R = c_i y_1 + d_i y_2$ and checked if its equal to $1$, in which case it's optimal (I used "efficient").

```python
r = c[i] * res[2] + d[i] * res[3]

if r == 1:
    eff += 1
else:
    not_eff += 1
```

since the problem is asking for different variations of the $c_i$ and $d_i$, I put this into a loop which keeps randomizing those parameters with different numbers of facilities.

```python
n = randint(4, 10)

a = [randint(1, 100) for _ in range(n)]
b = [randint(1, 100) for _ in range(n)]
c = [randint(1, 100) for _ in range(n)]
d = [randint(1, 100) for _ in range(n)]
```

after running it for a bit, the ratio of $\frac{efficient}{total}$ seemed to approach $0.38$.

---

the second question was what would happen if facilities with more than two inputs/outputs were considered. for this, I moved the script from having separate $a_i$/$b_i$/$c_i$/$d_i$ lists and instead having one list with all the parameters. calling it $e$ (creatively), this list is indexed like $e_j$ to get the $j$th parameter (first half are input params, second half are output params), and $e_{j_i}$ to get the $j$th parameter for the $i$th facility.

```python
n = randint(4, 10)
e = [[randint(1, 100) for _ in range(n)] for _ in range(m * 2)]
```

I updated the linear program optimization part accordingly.

```python
linprog(
    [0 for _ in range(m)] + [-1 * e[j + m][i] for j in range(m)],
    [
        # -- efficiency within 100%
        # E = (c_i y_1 + d_i y_1) / (a_i x_1 + b_i x_2)
        # E <= 1
        # c_i y_1 + d_i y_1 <= a_i x_1 + b_i x_2
        # -a_i x_1 -b_i x_2 + c_i y_1 + d_i y_1 <= 0
        [-1 * e[j][k] for j in range(m)] + [1 * e[j + m][k] for j in range(m)]
        for k in range(n)
    ] + [
        # -- fixed denominator
        # a_i x_1 + b_i x_2 = 1
        [ 1 * e[j][i] for j in range(m)] + [0 for _ in range(m)],
        [-1 * e[j][i] for j in range(m)] + [0 for _ in range(m)],
    ] + [
        # -- non-negative prices
        # x_1, x_2, y_1, y_2 >= 0
        [0] * j + [-1] + [0] * (m * 2 - j - 1)
        for j in range(m * 2)
    ],
    [0 for _ in range(n)] + [1, -1] + [0] * (m * 2),
    bounds=[(None, None)] * (m * 2),
)
```

similarly, $R$ becomes a sum over the output parameters and coordinating values.

```python
r = sum([e[j + m][i] * res[j + m] for j in range(m)])
```

in order to test out the different parameter counts, I looped over a range of $m$ values, which I used to mean the separate count of input/output parameters. putting the ratios I found in a spreadsheet gives this graph of $\frac{efficient}{total}$ for each param count.

![[dea.png]]

both scripts are in this github repo: https://github.com/ayukmr/dea. inside `src/dea`, `four.py` is for 2 params (4 in total) and `dynamic.py` is for any $m$ params.
