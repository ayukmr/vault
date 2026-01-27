# dp on grids

## finding maximum value in grid

can be done by going backwards based on directions

* start in bottom right, thought as $a[n][n]$
* evaluate $dp(i, j) = min(dp(i - 1, j), dp(i, j - 1))$, i.e. getting maximum value to get to that point
* repeat for those with memoization

## avoiding traps

* start in bottom right
* if $a[i - 1][j]$ is not trap, $dp(i, j)$ += $dp(i - 1, j)$ 
* if $a[i][j - 1]$ is not trap, $dp(i, j)$ += $dp(i, j - 1)$

## longest common subsequence

* representing as grid where row/col headers are compared and can 'skip' by going down rows
* i.e. if row/col not the same, set $dp(i, j)$ to $max(dp(i - 1, j), dp(i, j - 1))$. this is equivalent to skipping a character. if row/col are the same, set to $dp(i - 1, j - 1) + 1$, which is the equivalent to adding to the common subseq
