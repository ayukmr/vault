# more segtree apps

## finding $k$-th zero

* count numbers of zeros for each child
* start at root and descend based on what side $k$ would be on

## finding first $i$ where $a_i \ge x$

* create $\max$ segment tree
* start at root, if $l \ge x$ then descend $l$, else descend $r$
* repeat until base, finding $i$

## $k$th-smallest

* assemble $a$ as frequency array
* convert to bits; 1 for has $i$, 0 for no $i$

```cpp
int v = 1;

if (st[v] < k) return -1;

while (v < len) {
    if (st[v * 2] >= k) {
        v = v * 2;
    } else {
        k -= st[v * 2];
        v = v * 2 + 1;
    }
}

return v - len;
```

## contiguous blocks

* designate $0$s as empty and $1$s as full
* for each node, store max amount of consecutive $0$s ($seg$), maximum prefix of $0$s ($pref$), and maximum suffix of $0s$ ($suff$)
* can merge $pref$s and $suff$s together accordingly when moving up, so $seg = max(suff_l + pref_r, seg_l, seg_r)$
* for $pref$ and $suff$, based on if they're the entire length of the segment
    * if $pref_l = len_l$, $pref = pref_l + pref_r$, else $pref = pref_l$
    * if $suff_r = len_r$, $suff = suff_l + suff_r$, else $suff = suff_r$
