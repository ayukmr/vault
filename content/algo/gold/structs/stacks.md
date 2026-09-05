# stacks

last-in first-out structure (i.e. one-sided)

## nearest smaller element

finding closest element $j$ to left of some $i$ where $a_j < a_i$

* add pairs of $value$ and $index$ to stack
* remove from top of stack until top $value$ is less than current array $value$
* add top stack $index$ to $out$, add current array $value$ and $index$ to stack
