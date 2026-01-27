# finding shortest paths

## bellman-ford

* complexity: $\mathcal{O}(V \cdot E)$
* finding shortest path from node $x$ to other nodes, with negatives

```cpp
vector<long long> dist(n, INF);
dist[x] = 0;

for (int i = 0; i < n - 1; i++) {
    for (auto [a, b, w] : edges) {
        dist[b] = min(dist[b], dist[a] + w);
    }
}
```

## (pink) floyd-warshall

* complexity: $\mathcal{O}(V^3)$
* finding shortest path every node $x$ to every other node $y$

```cpp
vector<vector<long long>> dist(n, vector<long long>(n, INF));

for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        if (i == j) dist[i][j] = 0;
        else if (adj[i][j]) dist[i][j] = adj[i][j];
    }
}

for (int idt = 0; idt < n; idt++) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            dist[i][j] = min(dist[i][j], dist[i][idt] + dist[idt][j]);
        }
    }
}
```

## dijkstra

* complexity: $\mathcal{O}(E \cdot \log V)$
* finding shortest path from node $x$ to other nodes, without negatives

```cpp
vector<long long> dist(n, INF);
dist[x] = 0;

vector<bool> processed(n, false);

priority_queue<pair<int, int>> pq;
pq.push({0, x});

while (!pq.empty()) {
    int u = pq.top().second;
    pq.pop();

    if (processed[u]) continue;
    processed[u] = true;

    for (auto [v, w] : graph[u]) {
        if (dist[u] + w < dist[v]) {
            dist[v] = dist[u] + w;
            pq.push({-dist[v], v});
        }
    }
}
```
