--- 
# 3D Transformation Matrices

This document covers standard matrices for 3D transformations. For these examples, we assume column vectors and a right-handed coordinate system unless otherwise specified.

## 1. Identity Matrix

The identity matrix represents no transformation.

$$ I_3 =
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$

## 2. Translation Matrix

To represent translation with a matrix, we use homogeneous coordinates, which add a fourth component (`w`) to our 3D vectors. A 3D vector `(x, y, z)` becomes `(x, y, z, 1)`. The 3D translation matrix is a 4x4 matrix.

$$ T(t_x, t_y, t_z) =
\begin{bmatrix}
1 & 0 & 0 & t_x \\
0 & 1 & 0 & t_y \\
0 & 0 & 1 & t_z \\
0 & 0 & 0 & 1
\end{bmatrix}
$$

## 3. Scaling Matrix

Scaling changes the size of an object.

$$ S(s_x, s_y, s_z) =
\begin{bmatrix}
s_x & 0 & 0 \\
0 & s_y & 0 \\
0 & 0 & s_z
\end{bmatrix}
$$

In homogeneous coordinates, the 4x4 scaling matrix is:

$$ 
\begin{bmatrix}
s_x & 0 & 0 & 0 \\
0 & s_y & 0 & 0 \\
0 & 0 & s_z & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$ 

## 4. Axis-Aligned Rotation

These matrices rotate a point or object around one of the cardinal axes (X, Y, or Z).

### Rotation about the X-axis (Pitch)

This rotation is in the YZ plane.

*   **Right-Hand Rule (RHR):**
    $$ R_x(\theta) =
    \begin{bmatrix}
    1 & 0 & 0 \\
    0 & \cos\theta & -\sin\theta \\
    0 & \sin\theta & \cos\theta
    \end{bmatrix}
    $$ 

*   **Left-Hand Rule (LHR):**
    $$ R_x(\theta) =
    \begin{bmatrix}
    1 & 0 & 0 \\
    0 & \cos\theta & \sin\theta \\
    0 & -\sin\theta & \cos\theta
    \end{bmatrix}
    $$ 

### Rotation about the Y-axis (Yaw)

This rotation is in the ZX plane.

*   **Right-Hand Rule (RHR):**
    $$ R_y(\theta) =
    \begin{bmatrix}
    \cos\theta & 0 & \sin\theta \\
    0 & 1 & 0 \\
    -\sin\theta & 0 & \cos\theta
    \end{bmatrix}
    $$ 

*   **Left-Hand Rule (LHR):**
    $$ R_y(\theta) =
    \begin{bmatrix}
    \cos\theta & 0 & -\sin\theta \\
    0 & 1 & 0 \\
    \sin\theta & 0 & \cos\theta
    \end{bmatrix}
    $$ 

### Rotation about the Z-axis (Roll)

This rotation is in the XY plane.

*   **Right-Hand Rule (RHR):**
    $$ R_z(\theta) =
    \begin{bmatrix}
    \cos\theta & -\sin\theta & 0 \\
    \sin\theta & \cos\theta & 0 \\
    0 & 0 & 1
    \end{bmatrix}
    $$ 

*   **Left-Hand Rule (LHR):**
    $$ R_z(\theta) =
    \begin{bmatrix}
    \cos\theta & \sin\theta & 0 \\
    -\sin\theta & \cos\theta & 0 \\
    0 & 0 & 1
    \end{bmatrix}
    $$ 

## 5. Rotation Around an Arbitrary Axis

This is also known as Rodrigues' Rotation Formula. It rotates a vector by angle `θ` around an arbitrary unit axis `u = (x, y, z)`.

Let `c = cos(θ)` and `s = sin(θ)`. The rotation matrix is:

$$ R(\mathbf{u}, \theta) =
\begin{bmatrix}
c+x^2(1-c) & xy(1-c)-zs & xz(1-c)+ys \\
yx(1-c)+zs & c+y^2(1-c) & yz(1-c)-xs \\
zx(1-c)-ys & zy(1-c)+xs & c+z^2(1-c)
\end{bmatrix}
$$