# dp on ranges

## jazz 🎶

trying to find minimum insertions to balance string with omitted characters such that double letters are added like parens (i.e. not inside each other as `(){[}]` would be illegal, as `aabcbc` is)

* going from smallest to largest ranges of $[l, r]$
* simplest case is duplicating $s[l]$, meaning $dp[l][r] = dp[l + 1][r] + 1$
* if can pair $s[l]$ to some $s[k]$ within the range, then separate parts are the inside $[l + 1, k - 1]$ and outside after $[k + 1, r]$. thus, take $min(dp[l + 1][r] + 1, dp[l + 1][k - 1] + dp[k + 1][r])$ if pair is found
* answer is $dp[0][n - 1]$, finding min insertions in full range

## 3sum

[usaco.guide](https://usaco.guide/problems/usaco-994-3sum/solution)

finding number of triples in array that sum to zero

* count of ways $ways[i][j]$ is dependent on $ways[i + 1][j]$ and $ways[i][j - 1]$
* need to not to double count, so subtract $ways[i + 1][j - 1]$
* those ranges exclude the triple $(A_i, A_j, x)$, so need to include it
* frame as $ways[i][j] = ways[i + j][j] + ways[i][j - 1] - ways[i + 1][j - 1] + trp[i][j]$, where $trp[i][j]$ is amount of triples with $i$ and $j$
