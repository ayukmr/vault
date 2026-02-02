# binary indexed tree / fenwick tree

fast range sum queries while also being able to modify elements

```cpp
class BIT {
private:
    int len;
    vector<int> arr;
    vector<int> bit;

public:
    BIT(int n) : len(n), arr(n, 0), bit(n + 1, 0) {}

    BIT(const vector<int> &arr) : len(arr.size()), arr(len), bit(len + 1) {
        for (int i = 0; i < len; i++) {
            set(i, arr[i]);
        }
    }

    void set(int i, int x) {
        add(i, x - arr[i]);
    }

    void add(int i, int d) {
        arr[i] += d;
        for (i++; i <= len; i += i & -i) {
            bit[i] += d;
        }
    }

    int pref_sum(int i) {
        int s = 0;
        for (i++; i > 0; i -= i & -i) {
            s += bit[i];
        }
        return s;
    }

    int range(int a, int b) {
        return pref_sum(b) - (a > 0 ? pref_sum(a - 1) : 0);
    }
};
```
