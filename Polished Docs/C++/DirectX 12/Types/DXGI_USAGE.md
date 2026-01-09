
# DXGI_USAGE

The `DXGI_USAGE` enumeration contains flags that describe how a DXGI resource (like a texture or buffer) can be accessed and used by the CPU and GPU. These flags can be combined using a bitwise OR.

## Common Usage Flags

| Flag                            | Value        | Description                                       | Typical Use                               |
|---------------------------------|--------------|---------------------------------------------------|-------------------------------------------|
| `DXGI_USAGE_SHADER_INPUT`         | `0x00000010` | The resource can be bound as a shader input (Shader Resource View). | Textures or buffers read by shaders.     |
| `DXGI_USAGE_RENDER_TARGET_OUTPUT` | `0x00000020` | The resource can be bound as a render target (Render Target View). | Textures that the GPU will draw into.     |
| `DXGI_USAGE_UNORDERED_ACCESS`     | `0x00000400` | The resource can be bound for unordered access (Unordered Access View). | Buffers or textures for compute shaders. |
| `DXGI_USAGE_BACK_BUFFER`          | `0x00000040` | The resource is part of a swap chain's back buffer. | The primary output of a swap chain.     |
| `DXGI_USAGE_SHARED`               | `0x00000080` | The resource can be shared with other processes.  | Inter-process resource sharing.           |
| `DXGI_USAGE_READ_ONLY`            | `0x00000100` | The resource is marked as read-only.              | Depth-stencil buffers, read-only textures.|

---

## Recommended Usage by Resource Type

| Resource Type                 | Recommended DXGI_USAGE Flags                  |
|-------------------------------|-----------------------------------------------|
| Standard Texture (for reading)| `DXGI_USAGE_SHADER_INPUT`                       |
| Render Target Texture         | `DXGI_USAGE_RENDER_TARGET_OUTPUT` \| `DXGI_USAGE_SHADER_INPUT` |
| Swap Chain Buffer             | `DXGI_USAGE_RENDER_TARGET_OUTPUT` \| `DXGI_USAGE_BACK_BUFFER` |
| UAV / Compute Buffer          | `DXGI_USAGE_UNORDERED_ACCESS` \| `DXGI_USAGE_SHADER_INPUT` |
| Shared Texture                | `DXGI_USAGE_SHARED`                             |

**Note:** It is common to combine `DXGI_USAGE_RENDER_TARGET_OUTPUT` and `DXGI_USAGE_SHADER_INPUT` to allow a render target to be used as a texture in a subsequent pass (e.g., for post-processing).

---

## Special-Purpose Flags

| Flag                            | Value        | Description                                       | Notes                                     |
|---------------------------------|--------------|---------------------------------------------------|-------------------------------------------|
| `DXGI_USAGE_DISCARD_ON_PRESENT` | `0x00000200` | The resource's contents are discarded after being presented. | An optimization for swap chains.         |
| `DXGI_USAGE_GDI_COMPATIBLE`     | `0x00000800` | The resource can interoperate with Windows GDI.   | Rarely used in modern DirectX applications. |
