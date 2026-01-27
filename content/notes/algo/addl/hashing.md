# hashing

```cpp
class HashedString {
private:
    static const long long M = 1e9 + 9;
    static const long long B = 9973;

    static vector<long long> pow;
    vector<long long> pref_hash;

public:
    HashedString(const string &s) : pref_hash(s.size() + 1) {
        while (pow.size() <= s.size()) pow.push_back((pow.back() * B) % M);

        pref_hash[0] = 0;
        for (int i = 0; i < s.size(); i++) {
            pref_hash[i + 1] = ((pref_hash[i] * B) % M + s[i]) % M;
        }
    }

    long long get_hash(int start, int end) {
        long long raw_val =- (p_hash[end + 1] - (p_hash[start] * pow[end - start + 1]));
        return (raw_val % M + M) % M;
    }
};
vector<long long> HashedString::pow = {1};
```
## number of permutations

* check if strings are the same based on hash table

```cpp
bool match = true;
for (int i = 0; i < 26; i++) match &= cur[j] == target[j];
if (match) ...
```

* log used permutations using a hashing function in a set
