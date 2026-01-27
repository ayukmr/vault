# lazy segment tree

waste of time™

```cpp
class MaxSegmentTree {
private:
    int ident = -1e9;
    int len;
    vector<int> st;
    vector<int> lazy;

    void build(const vector<int> &arr, int v, int tl, int tr) {
        if (tl == tr) {
            st[v] = arr[tl];
            return;
        }
        int tm = (tl + tr) / 2;
        build(arr, v * 2, tl, tm);
        build(arr, v * 2 + 1, tm + 1, tr);
        st[v] = max(st[v * 2], st[v * 2 + 1]);
    }

    void push(int v) {
        st[v * 2] += lazy[v];
        lazy[v * 2] += lazy[v];
        st[v * 2 + 1] += lazy[v];
        lazy[v * 2 + 1] += lazy[v];
        lazy[v] = 0;
    }

    void update(int l, int r, int d, int v, int tl, int tr) {
        if (l > r) return;
        if (l == tl && r == tr) {
            st[v] += d;
            lazy[v] += d;
            return;
        }
        push(v);
        int tm = (tl + tr) / 2;
        update(l, min(r, tm), d, v * 2, tl, tm);
        update(max(l, tm + 1), r, d, v * 2 + 1, tm + 1, tr);
        st[v] = max(st[v * 2], st[v * 2 + 1]);
    }

    int range(int l, int r, int v, int tl, int tr) {
        if (l > r) return ident;
        if (l == tl && r == tr) return st[v];
        push(v);
        int tm = (tl + tr) / 2;
        int left = range(l, min(r, tm), v * 2, tl, tm);
        int right = range(max(l, tm + 1), r, v * 2 + 1, tm + 1, tr);
        return max(left, right);
    }

public:
    MaxSegmentTree(const vector<int> &arr)
        : len(arr.size()),
          st(len * 4, ident),
          lazy(len * 4, 0) {
        build(arr, 1, 0, len - 1);
    }

    void update(int l, int r, int d) {
        update(l, r, d, 1, 0, len - 1);
    }

    int range(int l, int r) {
        return range(l, r, 1, 0, len - 1);
    }
};
```
