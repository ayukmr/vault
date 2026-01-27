# dp using bitmasks

## removing from mask

taking problem buying $k$ products with different prices over $n$ days, have to buy each product once and trying to get min price

* for each day, with some remaining $S$, either choose to skip or buy an item based on min of previous $dp$ calls
* for buying an item, eval $min(dp(S \text{ without } x, d - 1) + price[x][d])$ for all $x$ that are in the current subset of items $S$
* for not buying an item, eval $dp(S, d - 1)$
* then, take $dp(S, d) = min($buying an item, not buying an item$)$

## elevator subsets

have some $n$ people with some weights $w[i]$, all need to go on elevator with max weight of $x$ while minimizing # of rides

* number of rides as $rides(S)$, amount of weight in current ride as $last(S)$, trying to minimize $rides$ then $last$
* observation: only last rider $r$ matters, so start with $\{rides(S \setminus r), last(S \setminus r)\}$
* if adding the rider weight to the current weight is less than $x$, make $dp(S) = min(dp(S), \{rides(S \setminus r), last(S \setminus r) + weight[r]\})$, comparing with last $dp(S)$ since trying all values $r$ in a loop
* else, if adding exceeds $x$, make $dp(S) = min(dp(S), \{rides(S \setminus r) + 1, weight[r]\})$, since making a new ride with $r$ in it.

## planes

directional graph of cities (flights), need to start at city $1$ and end at city $n$ while going through all $n$ cities

* define $dp(x, S)$ to be finding routes ending at $x$ using cities in $S$
* base case is $dp(1, \{1\}) = 1$
* $dp(x, S)$ += $dp(i, S \setminus x)$ for all $i$ that point to city $x$ in $S \setminus x$
* then, evaluate $dp(n, \{1..n - 1\})$ for solution
