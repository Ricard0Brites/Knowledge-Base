---
# Conventions in Transformation Matrices

Understanding the conventions used is crucial for correctly applying transformation matrices. Different software, libraries, and academic fields may use different conventions, leading to different matrix forms.

## Handedness of a Coordinate System

The "handedness" of a coordinate system determines the direction of the curl for a positive rotation. The two primary systems are the Right-Hand Rule (RHR) and the Left-Hand Rule (LHR).

### Right-Hand Rule (RHR)

The Right-Hand Rule is the most common convention in mathematics, linear algebra, and OpenGL.

*   **Definition**: If you point the thumb of your **right hand** along the positive direction of the rotation axis, the direction your fingers curl indicates the positive direction of rotation.
*   **Example**: When rotating around the Z-axis, a positive rotation moves a point on the X-axis towards the Y-axis. This appears as a **counter-clockwise** rotation when looking from the positive axis towards the origin.

### Left-Hand Rule (LHR)

The Left-Hand Rule is used in some systems, most notably DirectX.

*   **Definition**: If you point the thumb of your **left hand** along the positive direction of the rotation axis, the direction your fingers curl indicates the positive direction of rotation.
*   **Example**: When rotating around the Z-axis, a positive rotation moves a point on the X-axis away from the Y-axis. This appears as a **clockwise** rotation when looking from the positive axis towards the origin.

## Axis of Rotation

When discussing rotations in 3D, a rotation is performed *about* an axis. This rotation affects the other two axes.

| Axis of Rotation | Plane Being Rotated |
| :--------------: | :-----------------: |
|        X         |         YZ          |
|        Y         |         ZX          |
|        Z         |         XY          |

## Vector Notation: Column vs. Row

The layout of a matrix depends on whether you are using column vectors or row vectors.

*   **Column Vectors**: A vector `v` is represented as a column matrix. A transformation is applied by pre-multiplying the vector by the matrix: `v' = M * v`. This is the convention used in these documents.
*   **Row Vectors**: A vector `v` is represented as a row matrix. A transformation is applied by post-multiplying the vector by the matrix: `v' = v * M`. The matrix for a row-vector transformation is the transpose of the matrix for the equivalent column-vector transformation.