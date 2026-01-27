# topological sort

taking a DAG and making a vector such that parents always come before children

```cpp
vector<int> indeg(n);
for (const auto& nodes : graph) {
    for (int node : nodes) indeg[node]++;
}

queue<int> q;
for (int i = 0; i < n; i++) {
    if (indeg[i] == 0) q.push(i);
}

vector<int> sorted;
while (!q.empty()) {
    int u = q.front();
    q.pop();
    sorted.push_back(u);

    for (int v : graph[u]) {
        if (--indeg[v] == 0) q.push(v);
    }
}

if (sorted.size() != n) {
    // invalid
}
```
