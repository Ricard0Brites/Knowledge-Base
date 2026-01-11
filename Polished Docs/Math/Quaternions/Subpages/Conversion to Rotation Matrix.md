# Quaternion Conversion to Rotation Matrix (Right-Handed)

Given a unit quaternion $q = [w, x, y, z]$, the equivalent 3x3 rotation matrix is:

$$ 
*R* =
\begin{bmatrix}
1 - 2y^2 - 2z^2 & 2xy - 2zw & 2xz + 2yw \\
2xy + 2zw & 1 - 2x^2 - 2z^2 & 2yz - 2xw \\
2xz - 2yw & 2yz + 2xw & 1 - 2x^2 - 2y^2
\end{bmatrix}
$$