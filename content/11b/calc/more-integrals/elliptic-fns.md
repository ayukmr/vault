# elliptic functions

taking small sections that are diagonal lines from time $s$ to time $s + ds$

horizontally: $dx = x(s + ds) - x(s) = x'(s) ds$, i.e. change in $x$ for change in $t$ which is derivative
vertically: same thing, so $dy = y'(s)ds$

by pyth theorem, $dL$, infinitesimal portion of arc, is $\sqrt{(dx)^2 + (dy)^2}$, or $\sqrt{[x'(s)]^2 + [y'(s)]^2} ds$
trying to get full arc length; $L(t) = \int_0^t dL = \int_0^t \sqrt{[x'(s)]^2 + [y'(s)]^2} ds$

two particles:
1. $(x_1(s), y_1(s))$ using $x_1(s) = A \cos(s)$, $y_1(s) = A \sin(s)$ for some $A > 0$
2. $(x_2(s), y_2(s))$ using $x_2(s) = \cos(s)$, $y_2(s) = B \sin(s)$ for some $B > 1$
$L_1$ and $L_2$ are arc lengths for $x_1$, $y_1$ and $x_2$, $y_2$

---

for $t = 1$, for every $A$, is there a value $B$ such that $L_1(1) = L_2(1)$ 

![[elliptic-1.png]]

---

move to earlier time, e.g. $t = \frac{1}{2}$; is it still possible to find $B$ given $A$ so $L_1(\frac{1}{2}) = L_2(\frac{1}{2})$

seems to be the same as before? since both $L_1$ and $L_2$ share bounds for the integral and the shared values are because the expression within the integral was the same in the previous answer.

---

same thing, but with $t \rightarrow 0^+$

![[elliptic-2.png]]

---

for $t > 1$...

would still work with an arbitrary $t$? since all cases of this worked with different $t$s also, including the last one that also had a different solution using the limit
