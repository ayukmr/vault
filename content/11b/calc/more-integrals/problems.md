# problem set 3

## 1.

$\int_{-\pi/2}^0 e^q \sin(q) dq$

$f(q) = \sin(q)$
$g'(q) = e^q$

$\int f(q) g'(q) dq = f(q) g(q) - \int g(q) f'(q) dq$
$\int_{-\pi/2}^0 e^q \sin(q) dq = \sin(q)e^q - \int_{-\pi / 2}^0 e^q \cos(q) dq$

$\int_{-\pi / 2}^0 e^q \cos(q) dq$
$f(q) = \cos(q)$
$g'(q) = e^q$
$\int^0_{-\pi / 2} e^q \cos(q) dq = \cos(q) e^q + \int_{-\pi/2}^0 e^q \sin(q) dq$

$\int_{-\pi/2}^0 e^q \sin(q) dq = [\sin(q) e^q]_{-\pi/2}^0 - [\cos(q) e^q]_{\pi/2}^0 - \int_{-\pi/2}^0 e^q \sin(q) dq$
$2 \int_{-\pi/2}^0 e^q \sin(q) dq = [\sin(q) e^q]_{-\pi/2}^0 - [\cos(q) e^q]_{\pi/2}^0$

$[\sin(q) e^q]_{-\pi/2}^0 = \sin(0)e^0 - \sin(-\frac{\pi}{2})e^{-\pi/2} = e^{-\pi/2}$
$[\cos(q) e^q]_{-\pi/2}^0 = \cos(0)e^0 - \cos(-\frac{\pi}{2})e^{-\pi/2} = 1$

$2 \int_{-\pi/2}^0 e^q \sin(q) dq = e^{-\pi/2} - 1$
$\int_{-\pi/2}^0 e^q \sin(q) dq = \frac{e^{-\pi/2} - 1}{2}$

---

## 4.

$\int_0^{\pi/4} \sin(2 \theta) cos(2 \theta) d \theta$

$u = 2 \theta$
$\frac{d}{d \theta}[u] = \frac{d}{d \theta}[2 \theta]$
$\frac{du}{d \theta} = 2$
$d \theta = \frac{du}{2}$

$\int_0^{\pi/4} \sin(2 \theta) cos(2 \theta) d \theta = 2 \int_0^{\pi/2} \sin(u) \cos(u) du$

$f(u) = \sin(u)$
$g'(u) = \cos(u)$

$2 \int_0^{\pi/2} \sin(u) \cos(u) du = [\sin(u) \sin(u)]_0^{\pi/2} - \int_0^{\pi/2} \sin(u) \cos(u) du$

$3 \int_0^{\pi/2} \sin(u) \cos(u) du = [\sin^2(u)]_0^{\pi/2}$
$= \sin^2(\pi/2) - \sin^2(0)$
$= 1$

$\int_0^{\pi/2} \sin(u) \cos(u) du = \frac{1}{3}$
$\int_0^{\pi/4} \sin(2 \theta) \cos(2 \theta) d \theta = \frac{1}{3}$

---

## 23.

$\int \frac{1}{\sqrt{1 + e^x}} dx$

$u = \sqrt{1 + e^x}$
$\frac{du}{dx} = \frac{d}{dx}[\sqrt{1 + e^x}]$
$\frac{du}{dx} = \frac{1}{2}(1 + e^x)^{-\frac{1}{2}} \cdot (1 \cdot e^x)$
$du = \frac{e^x}{2\sqrt{1 + e^x}} dx$

$du = \frac{1}{\sqrt{1 + e^x}}dx \cdot \frac{e^x}{2}$
$du \cdot \frac{2}{e^x} = \frac{1}{\sqrt{1 + e^x}} dx$
$\int \frac{2}{e^x} du$

$u^2 = 1 + e^x$
$u^2 - 1 = e^x$
$\int \frac{2}{u^2 - 1} du$
$2 \int \frac{1}{u^2 - 1} du$

$\frac{1}{u^2 - 1} = \frac{1}{(u + 1)(u - 1)}$
$\frac{A}{u + 1} + \frac{B}{u - 1}$
$\frac{A(u - 1) + B(u + 1)}{(u + 1)(u - 1)}$

$A(u - 1)  + B(u + 1) = 1$
$Au - A + Bu + B = 1$
$(A + B)u + (-A + B)$

$A + B = 0$
$-A + B = 1$
$A = -0.5, B = 0.5$

$\frac{1}{u^2 - 1} = \frac{1}{2}(\frac{1}{u - 1} - \frac{1}{u + 1})$

$\int [\frac{1}{u - 1} - \frac{1}{u + 1}]du$
$\int \frac{1}{u - 1}du - \int \frac{1}{u + 1}du$
$\ln(|u - 1|) - \ln(|u + 1|)$
$\ln(|\sqrt{1 + e^x} - 1|) - \ln(|\sqrt{1 + e^x} + 1|)$
