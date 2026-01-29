# convergence

## harmonic series

$\sum^\infty_{n = 1} \frac{1}{n} = 1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \frac{1}{5} + \frac{1}{6} + \frac{1}{7} + \frac{1}{8} + \frac{1}{9} + \dots$

grouping by fractions that sum to $> \frac{1}{2}$
$\sum^\infty_{n = 1} \frac{1}{n} = 1 + \frac{1}{2} + (\frac{1}{3} + \frac{1}{4}) + (\frac{1}{5} + \frac{1}{6} + \frac{1}{7} + \frac{1}{8}) + \frac{1}{9} + \dots$
thus, doesn't converge as sum would be $> \frac{1}{2} \cdot \infty$

if series is converted to form harmonic series, can prove that that series also doesn't converge

## ratio test

$\rho = \lim_{n \rightarrow \infty}|\frac{a_{n + 1}}{a_n}|$
trying to make sure the limit ($\rho$) is $< 1$ for convergence

## comparison test

basically just the squeeze theorem
exists some $N$ s.t. $0 \le a_n \le b_n$ for all $n \ge N$. if $\sum b_n$ converges, $\sum a_n$ converges
exists some $N$ s.t. $a_n \ge b_n \ge 0$ for all $n \ge N$. if $\sum b_n$ diverges, $\sum a_n$ diverges

### with limits

if $\lim_{n \rightarrow \infty} \frac{a_n}{b_n} \ne 0$, then $\sum a_n$ and $\sum b_n$ both converge or both diverge
if $\lim_{n \rightarrow \infty} \frac{a_n}{b_n} = 0$ and $\sum b_n$ converges, then $\sum a_n$ converges
if $\lim_{n \rightarrow \infty} \frac{a_n}{b_n} = \infty$ and $\sum b_n$ diverges, then $\sum a_n$ diverges

## alternating series

$\sum^\infty_{n = 1} (-1)^{n + 1} b_n = b_1 - b_2 + b_3 - b_4$
or $\sum^\infty_{n} (-1)^{n + 1} b_n = b_1 - b_2 + b_3 - b_4$

converges if $0 \le b_{n + 1} \le b_n$ for all $n \le 1$
or if $\lim_{n \rightarrow \infty} b_n = 0$

$S_N$ is sum from $1 \rightarrow N$
$R_N$ is sum from $N + 1 \rightarrow \infty$
remainder $R_N = S - S_N$ satisfies $|R_N| \le b_{N + 1}$
since $R_N$ becomes smaller when $- b_n + b_{n + 1}$
