# union find / disjoint sets union

e.g. friends form alliances, alliances are mutual, need to query if $X$ and $Y$ are allied

* pick element to represent each set, i.e. friend $A$ and $B$ ally: $A \rightarrow B$, friend $C$ and $D$ ally: $C \rightarrow D$
* when joining sets, link representative of one to the other, i.e. $A \rightarrow B \leftarrow D \leftarrow C$
* then can query if in same set by finding lowest representative for each $X$ and $Y$

```cpp
class UnionFind {
private:
    vector<int> parent;
    vector<int> height;

public:
    UnionFind(int len) : parent(len), height(len, 1) {
        for (int i = 0; i < len; i++) parent[i] = i;
    }

    int find(int x) {
        while (x != parent[x]) parent[x] = find(parent[x]);
        return parent[x];
    }

    bool query(int x, int y) {
        return find(x) == find(y);
    }

    bool unite(int x, int y) {
        int xr = find(x);
        int yr = find(y);

        if (xr == yr) return false;
        if (height[yr] > height[xr]) swap(xr, yr);

        parent[yr] = xr;
        height[xr] += height[yr];

        return true;
    }
};
```
