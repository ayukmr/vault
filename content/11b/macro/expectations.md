# expectations and is-lm

* "current": current year
* "future": all future years

## $IS$

* starting with IS, $Y = C(Y - T) + I(Y, r) + G$
* define aggregate private spending as $A(Y, T, r) = C(Y - T) + I(Y, r)$
* then, get IS as $Y = A(Y, T, r) + G$ with $(+, -, -)$ relation

* extension is reliant on expected values, so $Y = A(Y, T, r, Y^{'e}, T^{'e}, r^{'e}) + G$ with $(+, -, -, +, -, -)$ relation
* curve is steeper than before but with same movement for current/expected deltas
![[expectations-1.png|400]]

* steep as changing current interest rate (y-axis) does not create large changes
    * given unchanged expectations in future interest rate, spending does not change by much. e.g. if current year interest rate goes from 5% -> 2% but rest of years are the same, not a large change overall
    * given unchanged expectations in future income, spending also does not change by much. e.g. if receiving money in an arbitrary instance with no expectations of future bonuses, will not cause large changes in spending (and thus multiplier is small)

## $LM$

* starting with LM, $\frac{M}{P} = YL(i)$
* distinction between $i$, nominal interest rate, and $r$, real interest rate
    * calculate real as $r = i - \pi^e$, same with expected $r^{'e} = i^{'e} - \pi^{'e}$
    * $\pi^e$ is expected inflation for current period, $\pi^{'e}$ is expected future inflation
* effects of central bank increasing money supply to decrease nominal $i$ depend on two factors
    * if increase in money supply leads financial markets to revise $i^{'e}$
    * if increase leads revising expected inflation, $\pi^e$ and $\pi^{'e}$
        * ignored for simplicity, so $\pi^e = 0$ and $\pi^{'e} = 0$ and $r = i$ and $r^{'e} = i^{'e}$
* gives $\frac{M}{P} = YL(r)$

## $IS$-$LM$

base curves
* steeper IS than before
![[expectations-2.png|400]]

expansionary monetary policy ($''$ used to differentiate with future $'$)
* central bank lowers interest rate by increasing money supply
    * gives intermediate equilibrium B
* expected values change accordingly
    * $Y^{'e} \uparrow$: expectation of higher future output
    * $r^{'e} \downarrow$: expectation of lower future interest rate
    * gives actual equilibrium C
![[expectations-3.png|400]]
