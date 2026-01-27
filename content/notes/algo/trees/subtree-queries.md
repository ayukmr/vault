# subtree queries

build a tree traversal array that contains nodes of rooted tree in dfs order. needs three values per node: $id$, $size$ (of subtree), $value$

```cpp
int ti = 0;

vector<int> start;
vector<int> end;

void euler_tour(int u, int p) {
    start[u] = ti++;
    for (int v : graph[u]) {
        if (v != p) euler_tour(u, v);
    }
    end[u] = ti;
}
```

## sums

* sums can be found under subtree based on position of $id$ and $size$
* can place traversal array into [segtree](../structs/segment-tree) and use range queries

```cpp
vector<long long> vals;

start.resize(n);
end.resize(n);
euler_tour(0, -1);

BIT bit(n);
for (int i = 0; i < n; i++) bit.set(start[i], vals[i]);

bit.set(u, x); // for some node u and val x
bit.range(start[u], end[u] - 1); // for some node u
```

## path traversal

* $value$ for nodes are distances from root
* access dist by finding $id$ and accessing $value$
* update dist by updating $value$ for node $i$ and all $i + size$ nodes after

```cpp
int ti = 0;

vector<int> dist;
vector<int> sz;
vector<int> pos;

void euler_tour(int u, int d, int p) {
    int start = ti++;
    pos[u] = start;
    dist[start] = d;
    for (auto [v, w] : graph[u]) {
        if (v != p) euler_tour(v, d + w, u);
    }
    sz[u] = ti - start;
}

dist.resize(n);
sz.resize(n);
pos.resize(n);
euler_tour(0, 0, -1);

dist[pos[u]]; // for some node u
for (int i = pos[u]; i < pos[u] + sz[u]; i++) dist[i] += d; // updating some node u by d
```
