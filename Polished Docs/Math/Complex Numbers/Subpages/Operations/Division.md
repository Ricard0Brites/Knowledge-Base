# Complex Number Division

Given two complex numbers $z_1 = a_1 + b_1i$ and $z_2 = a_2 + b_2i$ (where $z_2 \neq 0$), their quotient is found by multiplying the numerator and denominator by the [[Complex Conjugate and Modulus#Complex Conjugate|conjugate]] of the denominator:

$$ \frac{z_1}{z_2} = \frac{a_1 + b_1i}{a_2 + b_2i} \cdot \frac{a_2 - b_2i}{a_2 - b_2i} $$

$$ \frac{z_1}{z_2} = \frac{(a_1a_2 + b_1b_2) + (b_1a_2 - a_1b_2)i}{a_2^2 + b_2^2} $$

$$ \frac{z_1}{z_2} = \frac{a_1a_2 + b_1b_2}{a_2^2 + b_2^2} + \frac{b_1a_2 - a_1b_2}{a_2^2 + b_2^2}i $$

**Example:**
If $z_1 = 3 + 2i$ and $z_2 = 1 - 4i$:
$$ \frac{3 + 2i}{1 - 4i} = \frac{(3 + 2i)(1 + 4i)}{(1 - 4i)(1 + 4i)} = \frac{3 + 12i + 2i + 8i^2}{1^2 + (-4)^2} = \frac{3 + 14i - 8}{1 + 16} = \frac{-5 + 14i}{17} = -\frac{5}{17} + \frac{14}{17}i $$

Division is often simpler in [[Forms of Complex Numbers#2. Polar Form|Polar Form]]. If $z_1 = r_1 e^{i\theta_1}$ and $z_2 = r_2 e^{i\theta_2}$, then:
$$ \frac{z_1}{z_2} = \frac{r_1}{r_2} e^{i(\theta_1 - \theta_2)} $$
