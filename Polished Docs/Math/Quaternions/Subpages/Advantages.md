# Advantages of Quaternions

1.  **No Gimbal Lock**: Unlike Euler angles, quaternions do not suffer from gimbal lock, a phenomenon where two of the three rotation axes align, resulting in a loss of a degree of freedom.
2.  **Compact Storage**: Quaternions use 4 numbers to represent a rotation, which is more compact than a 3x3 rotation matrix (9 numbers).
3.  **Easy Interpolation**: Spherical Linear Interpolation (SLERP) for quaternions provides a smooth and consistent way to interpolate between two orientations, which is crucial for animations.
4.  **Efficient Concatenation**: Multiplying quaternions to combine rotations is generally more efficient than multiplying 3x3 matrices.
