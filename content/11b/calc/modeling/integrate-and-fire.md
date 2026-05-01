# integrate and fire

$V(t)$ is 'membrane potential' of a neuron
$f(V)$ is a decreasing linear fn of its current value, with $f(0) = 20V / sec$

neuron fires when $V(t) = V_{fire} = -0.05V$
afterwards, returns to resting value $V_{rest} = -0.075V$
baseline frequency of firing is $200Hz$

---

what should slope of $f(V)$ be?

$f(V) = mV + 20$
$\frac{dV}{dt} = mV + 20$

$dt = \frac{1}{mV + 20} dV$
$\int dt = \int \frac{1}{mV + 20} dV$

$\int \frac{1}{mV + 20} dV = \frac{1}{m} \ln|mV + 20|$
$t + C = \frac{1}{m} \ln|mV + 20|$
$mt + C = \ln|mV + 20|$
$e^{mt + C} = mV + 20$
$C e^{mt} = mV + 20$
$V(t) = \frac{C e^{mt} - 20}{m}$
$V(t) = Ce^{mt} - \frac{20}{m}$

$V(0) = V_0 = C e^{mt} - \frac{20}{m}$
$V_0 = C - \frac{20}{m}$
$C = V_0 + \frac{20}{m}$

$V(t) = (V_0 + \frac{20}{m}) e^{mt} - \frac{20}{m}$
assuming $V_0 = V_{rest}$
$V(t) = (-0.075 + \frac{20}{m}) e^{mt} - \frac{20}{m}$
and with $200Hz$

$V(\frac{1}{200}) = -0.05V = (-0.075 + \frac{20}{m}) e^{\frac{1}{200} m} - \frac{20}{m}$
$m = 231.278$

so $f(V) = 231.278V + 20$

---

how does firing frequency depend on $f(V)$?

$V(t) = (-0.075 + \frac{20}{m}) e^{mt} - \frac{20}{m}$
$\frac{V + \frac{20}{m}}{e^{mt}} = -0.075 + \frac{20}{m}$
$e^{mt} = \frac{V + \frac{20}{m}}{-0.075 + \frac{20}{m}}$
$t = \frac{\ln(\frac{V + \frac{20}{m}}{-0.075 + \frac{20}{m}})}{m}$

$t = \frac{\ln(\frac{V_{fire} + \frac{20}{m}}{-0.075 + \frac{20}{m}})}{m}$ for firing based on some slope $m$ for $f(V)$
