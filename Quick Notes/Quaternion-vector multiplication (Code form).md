If you have:

$$v = vector to rotate$$
$$q = rotation quaternion$$
Then the rotated vector is:
$$v' = v + 2 * cross(q_vec, cross(q_vec, v) + q.w * v)$$
Where $q_vec = (x, y, z)$ is the vector part of the quaternion.

Or, more commonly in engines like Unreal:

`FVector Rotated = Quat.RotateVector(OriginalVector);`

- The engine hides the algebra
    
- It’s equivalent to `q * v * q⁻¹`
    
- Preserves length exactly (unit quaternions!)