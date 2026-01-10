# Quaternions

Quaternions are a number system that extends complex numbers. In 3D graphics and other applications, they are primarily used to represent rotations. They offer several advantages over other rotation representations like Euler angles and rotation matrices.

## What are Quaternions?

A quaternion `q` is composed of a scalar part `w` and a vector part `(x, y, z)`. It can be written as:

$$
q = w + xi + yj + zk
$$

Where `i`, `j`, and `k` are imaginary units that satisfy the following rules:
*   $i^2 = j^2 = k^2 = ijk = -1$
*   $ij = k$, $jk = i$, $ki = j$
*   $ji = -k$, $kj = -i$, $ik = -j$

A unit quaternion (a quaternion with a magnitude of 1) can represent a 3D rotation. It is often represented as:

$$ 
q = [w, (x, y, z)] = [\cos(\theta/2), \mathbf{v}\sin(\theta/2)]
$$

Where `θ` is the angle of rotation, and `v` is the unit vector representing the axis of rotation.

## Advantages of Quaternions

1.  **No Gimbal Lock**: Unlike Euler angles, quaternions do not suffer from gimbal lock, a phenomenon where two of the three rotation axes align, resulting in a loss of a degree of freedom.
2.  **Compact Storage**: Quaternions use 4 numbers to represent a rotation, which is more compact than a 3x3 rotation matrix (9 numbers).
3.  **Easy Interpolation**: Spherical Linear Interpolation (SLERP) for quaternions provides a smooth and consistent way to interpolate between two orientations, which is crucial for animations.
4.  **Efficient Concatenation**: Multiplying quaternions to combine rotations is generally more efficient than multiplying 3x3 matrices.

## Basic Quaternion Operations

Let $q_1 = [w_1, \mathbf{v_1}]$ and $q_2 = [w_2, \mathbf{v_2}]$, where $\mathbf{v_1} = (x_1, y_1, z_1)$ and $\mathbf{v_2} = (x_2, y_2, z_2)$.

### 1. Addition (Component-wise)

$$ 
q_1 + q_2 = [w_1 + w_2, \mathbf{v_1} + \mathbf{v_2}] = [w_1+w_2, x_1+x_2, y_1+y_2, z_1+z_2]
$$

### 2. Multiplication (Non-commutative)

Quaternion multiplication is more complex and **not commutative** ($q_1 q_2 \neq q_2 q_1$).

$$ 
q_1 q_2 = [w_1w_2 - \mathbf{v_1} \cdot \mathbf{v_2}, w_1\mathbf{v_2} + w_2\mathbf{v_1} + \mathbf{v_1} \times \mathbf{v_2}]
$$

### 3. Conjugate

The conjugate of a quaternion `q = [w, (x, y, z)]` is:

$$ 
q^* = [w, -(x, y, z)] = [w, -\mathbf{v}]
$$

### 4. Magnitude (Norm)

The magnitude of a quaternion `q` is:

$$ 
||q|| = \sqrt{w^2 + x^2 + y^2 + z^2}
$$

For a unit quaternion, $||q|| = 1$.

### 5. Normalization

To normalize a quaternion, divide each component by its magnitude:

$$ 
\hat{q} = \frac{q}{||q||}
$$

### 6. Inverse

The inverse of a quaternion `q` is:

$$ 
q^{-1} = \frac{q^*}{||q||^2}
$$

For a unit quaternion, $q^{-1} = q^*$.

## Rotation with Quaternions

To rotate a 3D vector `p = (px, py, pz)` using a unit quaternion `q`:

1.  Convert the vector `p` into a "pure" quaternion (a quaternion with a zero scalar part): $p_q = [0, (p_x, p_y, p_z)]$
2.  Perform the rotation:
    $$ 
p'_q = q p_q q^{-1}
    $$
3.  The vector part of $p'_q$ will be the rotated vector $p'$.

## Conversion to Rotation Matrix (Right-Handed)

Given a unit quaternion $q = [w, x, y, z]$, the equivalent 3x3 rotation matrix is:

$$ 
R =
\begin{bmatrix}
1 - 2y^2 - 2z^2 & 2xy - 2zw & 2xz + 2yw \\
2xy + 2zw & 1 - 2x^2 - 2z^2 & 2yz - 2xw \\
2xz - 2yw & 2yz + 2xw & 1 - 2x^2 - 2y^2
\end{bmatrix}
$$ 

## Conversion from Rotation Matrix (Right-Handed)

Given a 3x3 rotation matrix:

$$ 
R =
\begin{bmatrix}
    R_{00} & R_{01} & R_{02} \\
    R_{10} & R_{11} & R_{12} \\
    R_{20} & R_{21} & R_{22}
\end{bmatrix}
$$ 

The quaternion components can be calculated as follows:

1.  Calculate the trace: $tr = R_{00} + R_{11} + R_{22}$
2.  If $tr > 0$:
    $S = \sqrt{tr + 1.0} \times 2$
    $w = 0.25 \times S$
    $x = (R_{21} - R_{12}) / S$
    $y = (R_{02} - R_{20}) / S$
    $z = (R_{10} - R_{01}) / S$
3.  Else if $R_{00} > R_{11}$ and $R_{00} > R_{22}$:
    $S = \sqrt{1.0 + R_{00} - R_{11} - R_{22}} \times 2$
    $w = (R_{21} - R_{12}) / S$
    $x = 0.25 \times S$
    $y = (R_{01} + R_{10}) / S$
    $z = (R_{02} + R_{20}) / S$
4.  Else if $R_{11} > R_{22}$:
    $S = \sqrt{1.0 + R_{11} - R_{00} - R_{22}} \times 2$
    $w = (R_{02} - R_{20}) / S$
    $x = (R_{01} + R_{10}) / S$
    $y = 0.25 \times S$
    $z = (R_{12} + R_{21}) / S$
5.  Else:
    $S = \sqrt{1.0 + R_{22} - R_{00} - R_{11}} \times 2$
    $w = (R_{10} - R_{01}) / S$
    $x = (R_{02} + R_{20}) / S$
    $y = (R_{12} + R_{21}) / S$
    $z = 0.25 \times S$

Remember to normalize the resulting quaternion to ensure it is a unit quaternion.