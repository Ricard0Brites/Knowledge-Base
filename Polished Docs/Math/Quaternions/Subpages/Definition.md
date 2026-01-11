
---

# What are Quaternions?

Quaternions are a number system that extends [[Complex Numbers|complex numbers]]. In 3D graphics and other applications, they are primarily used to represent rotations. They offer several advantages over other rotation representations like Euler angles and rotation matrices.

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

