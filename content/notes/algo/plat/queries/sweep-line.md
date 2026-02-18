# sweep line

## intersection points

* horizontal and vertical line segments, find number of intersection points

```cpp
int main() {
    int n;
    cin >> n;

    vector<array<int, 4>> ls;

    for (int i = 0; i < n; i++) {
        int x1, y1, x2, y2;

        cin >> x1 >> y1 >> x2 >> y2;
        x1 += 1e6; x2 += 1e6;

        if (y1 == y2) {
            ls.push_back({y1, 2, x1, x2});
        } else {
            ls.push_back({y1, 0, x1, x1});
            ls.push_back({y2, 1, x2, x2});
        }
    }
    sort(begin(ls), end(ls));

    BIT bit(2 * 1e6 + 1);
    long long ans;
    for (auto [y, ty, x1, x2] : ls) {
        if (ty == 0) {
            bit.add(x1, 1);
        } else if (ty == 1) {
            bit.add(x1, -1);
        } else {
            ans += bit.range(x1, x2);
        }
    }
}
```
