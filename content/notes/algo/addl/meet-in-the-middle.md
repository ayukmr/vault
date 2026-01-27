# meet in the middle

divide search space into two parts, combine results at the end

## sum to $x$

finding some numbers in list that sum to some $x$

* divide list in roughly half, creating two lists
* sum different subsets in each list
* choose single sum from each list and check if equals $x$

## xor paths

[codeforces](https://codeforces.com/contest/1006/problem/F)

finding paths from $0,0$ to $n,m$ that have every value xor'd together equal $k$

* find all $x,y$ positions reachable after half the moves from $0,0$ and $n,m$
* split problem calculating xors from $0,0 \rightarrow x,y$ and from $x,y \rightarrow n,m$
* for each $x,y$ then calculate $0,0 \rightarrow x,y \oplus x,y \rightarrow n,m$ and increment answers if equals $k$
