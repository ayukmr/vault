# dp on digits

## finding interesting numbers

abridged, find # of numbers between $0$ and $Y$ that fulfill cond that at least half of the number contains the same digit

* build numbers starting with the prefix
* with $pos$: position to add digit, $k$: balance of $target$ present (at end, non-negative achieves half cond), $under$: cond if under $Y$, $started$: if non-zero digit has been placed
* for each digit 0-9, pick as a $target$ for the entire dp run for solving $dp(pos: 0, k: 0, under: false, started: false)$, for the entire algorithm on a given $Y$
* for a given $dp$, try adding a digit 0-9 $i$ at $pos$. update $pos$ (inc), $under$ (if confirmed to be under $Y$), $started$ (if $i$ is non-zero). for $k$, if $i = target$, then inc, else decr. then calc $dp(pos, k, under, started)$ as sum of those
* duplicate handling omitted, basically checking for exactly half $i$ and half $j$ (counted as one by problem statement, counted as two by program)
