---
title: Tortoise and Hare Algorithm
tags:
  - algorithms
---

* Used for finding cycles in linked list in $O(n)$
* Uses two pointers, $slow$ and $fast$, pointing at head initially
* $slow$ moves one step, $fast$ moves two steps at a time
* Check if at any point both pointers point to same node
* Reset $slow$ back to head of linked list
* Move both pointers one step at a time
* The point they meet at is starting point of cycle

```python
# links
links = [1, 2, 3, 4, 5, 6, 2]

# list head
head = 0

slow = links[head]
fast = links[links[head]]

while slow != fast:
    # move slow once, fast twice
    slow = links[slow]
    fast = links[links[fast]]

# reset slow to head
slow = head

while slow != fast:
    # move both once
    slow = links[slow]
    fast = links[fast]

print(slow)
```
