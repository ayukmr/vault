# heavy-light decomposition

efficient path range queries with point updates on a tree

* $s(u)$ is size of subtree of node $u$
* dfs while marking one child node $v$ with the largest $s(v)$ as a heavy child
    * ties are broken arbitrarily, exactly 1 heavy child if $s(u) > 1$
* edges going to heavy childs are heavy edges, ones going to other childs are light edges
* heavy edges that connect to each other form heavy paths
* for each node, store top of heavy path as $head$ (non-heavy childs keep themselves as $head$)

* can prove that at most $\log n$ light edges will be crossed through by $s(v)$ doubling in size when going up
* indexing with a dfs, first visit heavy childs, meaning heavy path indexes will be contiguous
* build a [segtree](../structs/segment-tree) on the indexes, meaning heavy path queries can be done in $\log n$ (giving the other part of the $\mathcal{O}(\log^2n)$)

* trying to range query path from $a$ to $b$ can be split using [lca](../trees/least-common-ancestor), giving $a \rightarrow z$ and $b \rightarrow z$ as the ranges to find
* when going from node $u$ to $z$, use segtree range queries to compute value
* add $range(pos(head[u]), pos(u))$, jump to $parent[head[u]]$, repeat until reaching $z$

```cpp
template <typename T, typename Combine> class HLD {
private:
    int n, rt, ti = 0;
    vector<vector<int>> tree;
    vector<int> p, sz, depth, head, pos;
    T ident;
    Combine combine;
    SegmentTree<T, Combine> st;

    void dfs_sz(int v) {
        if (p[v] != -1) tree[v].erase(find(tree[v].begin(), tree[v].end(), p[v]));
        for (int &u : tree[v]) {
            p[u] = v;
            depth[u] = depth[v] + 1;
            dfs_sz(u);
            sz[v] += sz[u];
            if (sz[u] > sz[tree[v][0]]) swap(u, tree[v][0]);
        }
    }

    void dfs_hld(int v) {
        pos[v] = ti++;
        for (int u : tree[v]) {
            head[u] = u == tree[v][0] ? head[v] : u;
            dfs_hld(u);
        }
    }

public:
    HLD(vector<vector<int>> tree, int rt, T ident, Combine combine)
        : n(tree.size()), rt(rt), tree(tree),
          p(n, -1), sz(n, 1), depth(n), head(n), pos(n),
          ident(ident), combine(combine), st(vector<T>(n, ident), ident, combine) {
        head[rt] = rt;
        dfs_sz(rt);
        dfs_hld(rt);
    }

    T process(int a, int b) {
        T s = ident;
        for (; head[a] != head[b]; a = p[head[a]]) {
            if (depth[head[b]] > depth[head[a]]) swap(a, b);
            s = combine(s, st.range(pos[head[a]], pos[a]));
        }
        if (depth[b] > depth[a]) swap(a, b);
        s = combine(s, st.range(pos[b], pos[a]));
        return s;
    }

    void set(int i, T x) {
        st.set(pos[i], x);
    }
};
```
