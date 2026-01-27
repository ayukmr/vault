# lca

build a tree traversal array with node $id$ and depth, including circling back up. find node with minimum depth between two nodes to find least common ancestor. do fast rmqs using [segtree](../structs/segment-tree) or [sparse table](../structs/sparse-table)

```cpp
vector<pair<int, int>> depth;
vector<int> first;

void dfs(int u, int d) {
    if (first[u] == -1) first[u] = depth.size();
    depth.push_back({d, u});

    for (int v : graph[u]) {
        dfs(v, d + 1);
        depth.push_back({d, u});
    }
}

first.assign(n, -1);
dfs(0, 0);

auto combine = [](pair<int, int> a, pair<int, int> b) { return min(a, b); };
SparseTable<pair<int, int>, decltype(combine)> st(depth, combine);

// lca of some nodes x and y
int l = first[x];
int r = first[y];
if (l > r) swap(l, r);
int lca = st.range(l, r).second;
```

## distances between nodes

with $c$ as lca of nodes $a$ and $b$, can compute distance using formula $depth(a) + depth(b) - 2 \cdot depth(c)$

## milk visits

* run dfs for lca
* while running, store list of changes of type $c$ at each entry/exit time point as $\{t, \text{lowest node of type } c \text{ at that point}\}$
* get lca for nodes $a$ and $b$
* define $last(a, c)$ as getting lowest node of type $c$ when dfs was at $a$, by finding the pair with the greatest $t <= \text{entry time for } a$, i.e. `upper_bound`
* get the depth of that lowest node and check if that $depth >= \text{depth of the } lca$
* if it is, then the condition succeeds, since there is a $c$ node on the path between $a$ and the $lca$
* repeat these same steps for the other node $b$
