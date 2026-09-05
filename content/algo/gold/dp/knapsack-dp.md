# knapsack problem

## finding minimum to make some $N$

follows the form of $dp(N) = min(dp(N - x_1), dp(N - x_2)...) + 1$ when getting minimum required to make some value $N$, like in the coin adding problem

## finding # of sequences that make some $N$

looks like $dp(N) = dp(N - x_1) + dp(N - x_2)...$ when getting all combinations to add up to something, like in dice adding problem
