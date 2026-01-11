# Quaternion Rotation

To rotate a 3D vector `p = (px, py, pz)` using a unit quaternion `q`:

1.  Convert the vector `p` into a "pure" quaternion (a quaternion with a zero scalar part): $p_q = [0, (p_x, p_y, p_z)]$
2.  Perform the rotation:
    $$ 
    p'_q = q p_q q^{-1}
    $$
3.  The vector part of $p'_q$ will be the rotated vector $p'$.
