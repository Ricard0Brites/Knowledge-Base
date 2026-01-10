# Descriptor Types

### CBV — Constant Buffer View
*   **Purpose**: Provides read-only access to shader constants (e.g., matrices, material properties).
*   **Data**: Backed by a `ID3D12Resource` buffer.
*   **Constraints**: Must be 256-byte aligned.

### SRV — Shader Resource View
*   **Purpose**: Provides read-only access to resources like textures and structured buffers.
*   **Data**: Textures (2D, 3D, Cube), buffers.
*   **Use Case**: Sampling textures, reading from data buffers.

### UAV — Unordered Access View
*   **Purpose**: Provides read-write access to resources from shaders.
*   **Data**: RW textures, RW structured buffers.
*   **Use Case**: Compute shader outputs, read/write operations in pixel shaders.
*   **Features**: Supports atomic operations.

![[Pasted image 20260110173049.png]]

### Comparison

| View | Read | Write | Typical Use |
|---|---|---|---|
| CBV | Yes | No | Small, constant data blocks. |
| SRV | Yes | No | Textures, read-only buffers. |
| UAV | Yes | Yes| Compute outputs, RW textures. |
