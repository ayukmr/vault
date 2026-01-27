# minimum spanning trees

turning (dense) connected graph into tree where sum of weights is minimized

## kruskal's

```cpp
vector<tuple<int, int, int>> se = edges;

sort(se.begin(), se.end(), [](const auto& x, const auto& y) {
    return get<2>(x) < get<2>(y);
});

vector<tuple<int, int, int>> mst;
long long total = 0;
UnionFind uf(n);

for (auto e : se) {
    auto [a, b, w] = e;

    if (!uf.query(a, b)) {
        uf.unite(a, b);
        mst.push_back(e);
        total += w;
    }
}
```

## prim's

mostly just less readable but doesn't depend on [union-find](union-find)

```cpp
vector<int> parent(n, -1);
long long total = 0;

priority_queue<tuple<int, int, int>> pq;
pq.push({0, 0, 0});

while (!pq.empty()) {
    auto [nw, p, u] = pq.top();
    pq.pop();

    if (parent[u] != -1) continue;

    parent[u] = p;
    total += -nw;

    for (auto [v, w] : graph[u]) {
        if (parent[u] == -1) pq.push({-w, u, v});
    }
}
```
