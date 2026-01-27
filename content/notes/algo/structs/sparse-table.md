# sparse table

for O(1) [LCA](../trees/least-common-ancestor), no clue how it works

```cpp
template <typename T, typename Combine>
class SparseTable {
private:
    int n, log2dist;
    Combine combine;
    vector<vector<T>> st;

public:
    SparseTable(const vector<T> &v, Combine combine) : combine(combine) {
        n = v.size();
        log2dist = 1 + (int) log2(n);
        st.resize(log2dist);
        st[0] = v;

        for (int i = 1; i < log2dist; i++) {
            st[i].resize(n - (1 << i) + 1);
            for (int j = 0; j + (1 << i) <= n; j++) {
                st[i][j] = combine(st[i - 1][j], st[i - 1][j + (1 << (i - 1))]);
            }
        }
    }

    T range(int l, int r) {
        int i = (int) log2(r - l + 1);
        return combine(st[i][l], st[i][r - (1 << i) + 1]);
    }
};
```
