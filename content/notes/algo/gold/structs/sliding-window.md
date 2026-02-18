# sliding window

## two pointers

finding maximum length in array without repeats

* maintain $start$ and $end$ pointers
* increment $end$ while adding values to a set to check for repeats
* when repeat is found, update maximum length
* then, increment $start$ until clear of repeat

## O(N) sliding window min

modifying deque to store minimums

```cpp
deque<int> wq;

int winmin() {
  return wq.front();
}

void winadd(int x) {
    while (!wq.empty() && wq.back() > x) wq.pop_back();
    wq.push_back(x);
}

void winrm(int x) {
    if (!wq.empty() && wq.front() == x) wq.pop_front();
}
```

move across array while inserting $a_i$ and removing $a_{i - k}$ and take minimum of each window
