A **direction vector**, e.g., “forward” in local space:

`Forward = (1, 0, 0)  // engine convention, usually X-forward`

You want:

`RotatedForward = q * Forward * q⁻¹`