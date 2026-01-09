---
# Projection Matrices

Projection matrices are used to transform 3D coordinates into a 2D space, such as a screen. There are two main types of projection: orthographic and perspective.

## 1. Orthographic Projection

Orthographic projection maps 3D coordinates to 2D coordinates without any sense of depth or perspective. Objects appear the same size regardless of their distance from the camera. It is often used in technical drawings, architectural plans, and some stylized video games.

### Simple 3D to 2D Orthographic Projection

This matrix discards the z-coordinate, effectively projecting the 3D space onto the XY plane.

$$
P_{\text{ortho}} =
\begin{bmatrix}
1 & 0 & 0 \
0 & 1 & 0
\end{bmatrix}
$$

### 3D Orthographic Projection (Homogeneous Coordinates)

This matrix maps a 3D rectangular volume (a "box") into a canonical view volume, typically a cube from (-1, -1, -1) to (1, 1, 1). This is the form commonly used in graphics APIs like OpenGL.

$$
P_{\text{ortho}} =
\begin{bmatrix}
\frac{2}{r-l} & 0 & 0 & -\frac{r+l}{r-l} \
0 & \frac{2}{t-b} & 0 & -\frac{t+b}{t-b} \
0 & 0 & \frac{-2}{f-n} & -\frac{f+n}{f-n} \
0 & 0 & 0 & 1
\end{bmatrix}
$$

Where:
*   `l`, `r`: Coordinates for the left and right vertical clipping planes.
*   `b`, `t`: Coordinates for the bottom and top horizontal clipping planes.
*   `n`, `f`: Distances to the near and far depth clipping planes.

## 2. Perspective Projection

Perspective projection simulates how objects appear to the human eye: objects farther away appear smaller. This is the most common projection used in 3D games and realistic rendering.

The projection transforms a frustum (a truncated pyramid) of the 3D world into the canonical view volume.

### Perspective Projection Matrix (Right-Handed, OpenGL-style)

This matrix is for a right-handed coordinate system, where the camera is looking down the -Z axis.

$$ P_{\text{persp}} =
\begin{bmatrix}
\frac{e_x}{a} & 0 & 0 & 0 \
0 & e_y & 0 & 0 \
0 & 0 & \frac{f+n}{n-f} & \frac{2fn}{n-f} \
0 & 0 & -1 & 0
\end{bmatrix}
$$

Where:
*   `a` = Aspect ratio of the viewport (`width / height`).
*   `θ` = The vertical field of view (FOV) angle.
*   `e_y = 1 / tan(θ / 2)` is the y-scaling factor.
*   `e_x = e_y / a` is the x-scaling factor.
*   `n` = Distance to the near clipping plane.
*   `f` = Distance to the far clipping plane.

**Note**: The specific form of the perspective matrix can vary significantly between different graphics APIs (like OpenGL and DirectX) due to differences in coordinate system conventions (handedness and direction of the depth buffer).