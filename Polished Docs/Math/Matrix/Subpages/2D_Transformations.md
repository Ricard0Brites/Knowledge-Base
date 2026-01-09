---
# 2D Transformation Matrices

This document covers standard matrices for 2D transformations. For these examples, we assume column vectors and a right-handed coordinate system.

## 1. Identity Matrix

The identity matrix represents no transformation. Multiplying any matrix by the identity matrix results in the original matrix.

$$ I_2 =
\begin{bmatrix}
1 & 0 \
0 & 1
\end{bmatrix}
$$

## 2. Translation Matrix

Translation moves an object without changing its orientation or size. To represent translation with a matrix, we use homogeneous coordinates, which add a third component (`w`) to our 2D vectors. A 2D vector `(x, y)` becomes `(x, y, 1)`.

The 2D translation matrix is a 3x3 matrix.

$$ T(t_x, t_y) =
\begin{bmatrix}
1 & 0 & t_x \
0 & 1 & t_y \
0 & 0 & 1
\end{bmatrix}
$$

Where `tx` and `ty` are the distances to move along the x and y axes, respectively.

## 3. Scaling Matrix

Scaling changes the size of an object. The scaling matrix is a 2x2 matrix.

$$ S(s_x, s_y) =
\begin{bmatrix}
s_x & 0 \
0 & s_y
\end{bmatrix}
$$

Where `sx` and `sy` are the scaling factors for the x and y axes. Values greater than 1 will enlarge the object, while values between 0 and 1 will shrink it.

In homogeneous coordinates, the 3x3 scaling matrix is:

$$ S(s_x, s_y) =
\begin{bmatrix}
s_x & 0 & 0 \
0 & s_y & 0 \
0 & 0 & 1
\end{bmatrix}
$$

## 4. Rotation Matrix

Rotation moves a point around a center (usually the origin). The 2D rotation matrix for a counter-clockwise rotation by an angle `θ` is:

$$ R(\theta) =
\begin{bmatrix}
\cos\theta & -s\sin\theta \
\sin\theta & \cos\theta
\end{bmatrix}
$$

This is the standard Right-Hand Rule rotation matrix. The Left-Hand Rule matrix would have the sign of the `sin` terms flipped.

**HLSL Code for 2D Rotation (Column Vectors)**

```hlsl
// Right-Hand Rule (counter-clockwise)
float2x2 rhr_rotation(float angle) {
    float c = cos(angle);
    float s = sin(angle);
    return float2x2(
        c, -s,
        s,  c
    );
}

// Left-Hand Rule (clockwise)
float2x2 lhr_rotation(float angle) {
    float c = cos(angle);
    float s = sin(angle);
    return float2x2(
        c,  s,
       -s,  c
    );
}
```

## 5. Shear Matrix

A shear transformation slants the shape of an object.

$$ \text{Sh} =
\begin{bmatrix}
1 & sh_x \
sh_y & 1
\end{bmatrix}
$$

- `sh_x` shears the object along the x-axis.
- `sh_y` shears the object along the y-axis.

## 6. Reflection Matrix

Reflection flips an object across a line.

*   **Reflection across the Y-axis**:
    $$ \begin{bmatrix}
    -1 & 0 \
    0 & 1
    \end{bmatrix}
    $$

*   **Reflection across the X-axis**:
    $$ \begin{bmatrix}
    1 & 0 \
    0 & -1
    \end{bmatrix}
    $$