---
# Advanced Transformation Topics

This document covers more advanced concepts related to transformation matrices.

## 1. Composite Transformations

A composite transformation is the result of applying multiple transformations in sequence. This is achieved by multiplying the individual transformation matrices together.

The order of matrix multiplication is important. Since we use column vectors, the transformations are applied from right to left. For example, to first scale an object, then rotate it, and finally translate it, the combined matrix `M` would be:

$$ M = T \cdot R \cdot S $$

When this matrix is applied to a vector `v`, the scaling is applied first:

$$ \mathbf{v'} = (T \cdot R \cdot S) \mathbf{v} = T(R(S\mathbf{v})) $$

## 2. Change of Basis (Coordinate System Change)

A transformation matrix can be used to change the coordinate system of a vector. This is also known as a "change of basis".

Let's say you have a set of basis vectors `b1`, `b2`, and `b3` that define a new coordinate system (e.g., the local space of an object) within the world coordinate system. You can create a matrix `B` by using these basis vectors as its columns:

$$ B =
\begin{bmatrix}
| & | & | \\
\mathbf{b_1} & \mathbf{b_2} & \mathbf{b_3} \\
| & | & | 
\end{bmatrix}
$$ 

*   **To transform a vector from the local coordinate system to the world coordinate system**, you multiply the vector by this basis matrix `B`:
    $$ \mathbf{v}_{\text{world}} = B \cdot \mathbf{v}_{\text{local}} $$

*   **To transform a vector from the world coordinate system to the local coordinate system**, you multiply the vector by the inverse of the basis matrix, `B⁻¹`:
    $$ \mathbf{v}_{\text{local}} = B^{-1} \cdot \mathbf{v}_{\text{world}} $$
    If the basis vectors are orthonormal (they are mutually perpendicular and have a length of 1), the matrix is orthogonal, and its inverse is simply its transpose: `B⁻¹ = Bᵀ`.

## 3. Normal Matrix

When applying a non-uniform scale to a model, the model's normals (vectors perpendicular to the surface, used for lighting calculations) cannot be transformed by the same matrix as the vertices. If they are, they will no longer be perpendicular to the surface.

The correct way to transform normals is to use the **inverse transpose** of the model's transformation matrix. This is called the "normal matrix".

$$ N = (M^{-1})^T $$

Where `M` is the upper 3x3 portion of the model's transformation matrix (we don't care about the translation part for normals).

If the transformation `M` only contains uniform scaling and rotations, then `M` is an orthogonal matrix. In this case, `(M⁻¹)^T = M`, so you can use the model matrix directly. However, it is safer to use the inverse transpose to handle all cases correctly.