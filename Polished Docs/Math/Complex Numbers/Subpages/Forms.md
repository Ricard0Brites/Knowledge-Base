# Forms of Complex Numbers

Complex numbers can be represented in several forms, each offering different advantages for specific operations and contexts.

## 1. Cartesian (Rectangular) Form

The most common way to express a complex number `z` is in its Cartesian form:

$$ z = a + bi $$

Where:
*   `a` is the real part, plotted on the horizontal axis.
*   `b` is the imaginary part, plotted on the vertical axis.
*   `i` is the imaginary unit, satisfying $i^2 = -1$.

This form is particularly useful for addition and subtraction of complex numbers.

## 2. Polar Form

The polar form represents a complex number `z` by its magnitude (or modulus) `r` and its argument (or angle) `θ`.

$$ z = r(\cos \theta + i \sin \theta) $$

Where:
*   `r` is the distance from the origin to the point `(a, b)` in the complex plane, $r = |z| = \sqrt{a^2 + b^2}$.
*   `θ` is the angle (in radians) between the positive real axis and the line segment from the origin to `(a, b)`, $\theta = \arg(z)$. This angle is usually given in the interval $(-\pi, \pi]$ or $[0, 2\pi)$.

Conversion from Cartesian to Polar:
r = $\sqrt{a^2 + b^2}$
$\theta = \operatorname{atan2}(b, a)$

Conversion from Polar to Cartesian:
a = r $\cos \theta$
b = r $\sin \theta$

The polar form simplifies multiplication and division of complex numbers.

## 3. Exponential Form (Euler's Form)

The exponential form is a concise representation derived from Euler's formula, which states:

$$ e^{i\theta} = \cos \theta + i \sin \theta $$

Using this, the polar form can be rewritten as:

$$ z = r e^{i\theta} $$

This form is highly convenient for operations involving powers and roots of complex numbers, and it elegantly shows the relationship between exponential functions and trigonometry.
