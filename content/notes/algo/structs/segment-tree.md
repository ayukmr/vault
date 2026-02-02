# segment tree

tree with array nodes on the bottom level with hierarchy of nodes containing information built on top. e.g. for sums, layer $0$ is array, layer $1$ is sum of every two elements, layer $2$ is sum of every two elements from layer $1$, etc.

nodes are stored in a flat array, where parent of $k$ is $\lfloor k/2 \rfloor$ and children are $2k$ and $2k + 1$. therefore, if position of node is even it is a left child, and odd means a right child.

* with some range from $a$ to $b$, start by adding $n$ to get indexes (since adding $n$ moves to the base array indexes within the full node array)
* if $a$ is odd, its parent will include something outside of the range (since odd means right child, and the parent also includes the left child)
* if $b$ is even, same concept applies, but parent will include right child which is outside of the range
* continually divide both $a$ and $b$ by $2$ to get to their parents (based on $\lfloor k/2 \rfloor$)

## v1 (iterative)

```cpp
template <typename T, typename Combine>
class SegmentTree {
private:
    T ident;
    int len;
    vector<T> st;
    Combine combine;

    int next_pow2(int len) {
        len--;
        len |= len >> 1;
        len |= len >> 2;
        len |= len >> 4;
        len |= len >> 8;
        len |= len >> 16;
        return len + 1;
    }

    void build(const vector<T> &arr) {
        copy(arr.begin(), arr.end(), st.begin() + len);
        for (int i = len - 1; i >= 1; i--) {
            st[i] = combine(st[i * 2], st[i * 2 + 1]);
        }
    }

public:
    SegmentTree(const vector<T> &arr, T ident, Combine combine)
        : ident(ident),
          len(next_pow2(arr.size())),
          st(len * 2, ident),
          combine(combine) {
        build(arr);
    }

    void set(int i, T x) {
        i += len;
        st[i] = x;
        for (i /= 2; i >= 1; i /= 2) {
            st[i] = combine(st[i * 2], st[i * 2 + 1]);
        }
    }

    T range(int l, int r) {
        l += len;
        r += len;

        T s = ident;
        while (l <= r) {
            if (l % 2 == 1) s = combine(s, st[l++]);
            if (r % 2 == 0) s = combine(s, st[r--]);
            l /= 2;
            r /= 2;
        }
        return s;
    }
};
```

## recursive (v2, for [lazy](../plat/lazy-segment-tree))

```cpp
template <typename T, typename Combine>
class SegmentTree {
private:
    T ident;
    int len;
    vector<T> st;
    Combine combine;

    void build(const vector<T> &arr, int v, int tl, int tr) {
        if (tl == tr) {
            st[v] = arr[tl];
            return;
        }
        int tm = (tl + tr) / 2;
        build(arr, v * 2, tl, tm);
        build(arr, v * 2 + 1, tm + 1, tr);
        st[v] = combine(st[v * 2], st[v * 2 + 1]);
    }

    void update(int i, T x, int v, int tl, int tr) {
        if (tl == tr) {
            st[v] = x;
            return;
        }
        int tm = (tl + tr) / 2;
        if (i <= tm) update(i, x, v * 2, tl, tm);
        else update(i, x, v * 2 + 1, tm + 1, tr);
        st[v] = combine(st[v * 2], st[v * 2 + 1]);
    }

    T range(int l, int r, int v, int tl, int tr) {
        if (tr < l || tl > r) return ident;
        if (l <= tl && r >= tr) return st[v];
        int tm = (tl + tr) / 2;
        T left = range(l, r, v * 2, tl, tm);
        T right = range(l, r, v * 2 + 1, tm + 1, tr);
        return combine(left, right);
    }

public:
    SegmentTree(const vector<T> &arr, T ident, Combine combine)
        : ident(ident),
          len(arr.size()),
          st(len * 4, ident),
          combine(combine) {
        build(arr, 1, 0, len - 1);
    }

    void set(int i, T x) {
        update(i, x, 1, 0, len - 1);
    }

    T range(int l, int r) {
        return range(l, r, 1, 0, len - 1);
    }
};
```
