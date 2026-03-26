# trig substitution

$\int \sqrt{1  - x^2} dx$
$x = \sin t$
$dx = \cos t dt$

$= \int \cos^2 t dt$

$\cos 2 \theta = \cos^2 \theta - \sin^2 \theta$
$= \cos^2 \theta - (1 - \cos^2 \theta)$
$= 2 \cos^2 \theta - 1$

$\cos^2 \theta = \frac{\cos 2 \theta + 1}{2}$

$= \frac{1}{2} \int [\cos 2t + 1]dt$

$u = 2t$
$du = 2dt$
$dt = \frac{du}{2}$

$= \frac{1}{2} \int [\cos u + 1] \frac{du}{2}$
$= \frac{1}{4} \int [\cos u + 1] du$

$= \frac{1}{4}(\sin u + u)$
$= \frac{1}{4}(\sin 2t + 2t)$

$t = \sin^{-1} x$

$= \frac{1}{4}(\sin(2 \sin^{-1} x) + 2 \sin^{-1} x)$
