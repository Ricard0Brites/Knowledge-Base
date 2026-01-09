
# DXGI_FORMAT

`DXGI_FORMAT` is an enumeration that specifies the data format of a resource, such as a texture or buffer. It defines how the data in memory should be interpreted by the GPU.

## Common Format Categories

### 1. Typeless Formats
These formats define the memory layout without specifying the data type (e.g., float, UNORM, SNORM). This allows a resource to be interpreted in different ways.
- `DXGI_FORMAT_R32G32B32A32_TYPELESS`
- `DXGI_FORMAT_R24G8_TYPELESS` (for depth-stencil)

### 2. Float Formats
Used for high-precision data like HDR render targets or G-buffer positions.
- `DXGI_FORMAT_R32G32B32A32_FLOAT` (128-bit)
- `DXGI_FORMAT_R16G16B16A16_FLOAT` (64-bit, "half" precision)
- `DXGI_FORMAT_R11G11B10_FLOAT` (32-bit packed float)

### 3. Normalized Formats (UNORM / SNORM)
These formats map integer values to a floating-point range.
- **UNORM** (Unsigned Normalized): Maps to `[0.0, 1.0]`. Used for standard color textures.
- **SNORM** (Signed Normalized): Maps to `[-1.0, 1.0]`. Used for normal maps.

**Examples:**
- `DXGI_FORMAT_R8G8B8A8_UNORM` (standard 32-bit color)
- `DXGI_FORMAT_R8G8B8A8_UNORM_SRGB` (sRGB gamma corrected color)
- `DXGI_FORMAT_R16G16_SNORM` (high-quality normal maps)

### 4. Integer Formats (UINT / SINT)
Used for non-color data like indices, masks, or structured data in compute shaders.
- `DXGI_FORMAT_R32G32B32A32_UINT`
- `DXGI_FORMAT_R8_UINT`

### 5. Depth-Stencil Formats
Special formats used for depth and stencil buffers, which are essential for 3D depth testing and masking.
- `DXGI_FORMAT_D32_FLOAT` (32-bit depth)
- `DXGI_FORMAT_D24_UNORM_S8_UINT` (24-bit depth, 8-bit stencil)

### 6. Compressed Formats (BC - Block Compression)
These formats reduce memory and bandwidth usage by storing texture data in compressed blocks.
- `DXGI_FORMAT_BC1_UNORM` (DXT1): For diffuse textures without alpha.
- `DXGI_FORMAT_BC3_UNORM` (DXT5): For diffuse textures with alpha.
- `DXGI_FORMAT_BC5_SNORM`: For normal maps (two-channel).

<details>
<summary><b>Complete DXGI_FORMAT Reference Table</b></summary>

|Format|Components|Bits per Channel|Type|Memory Layout|Use|
|---|---|---|---|---|---|
|`DXGI_FORMAT_UNKNOWN`|-|-|-|-|Undefined / placeholder|
|`DXGI_FORMAT_R32G32B32A32_TYPELESS`|RGBA|32|Typeless|128-bit|Typed later (float/int)|
|`DXGI_FORMAT_R32G32B32A32_FLOAT`|RGBA|32|Float|128-bit|HDR rendering, G-buffer|
|`DXGI_FORMAT_R32G32B32A32_UINT`|RGBA|32|UInt|128-bit|Structured buffers|
|`DXGI_FORMAT_R32G32B32A32_SINT`|RGBA|32|SInt|128-bit|Compute buffers|
|`DXGI_FORMAT_R32G32B32_TYPELESS`|RGB|32|Typeless|96-bit|Typed later|
|`DXGI_FORMAT_R32G32B32_FLOAT`|RGB|32|Float|96-bit|High-precision vectors|
|`DXGI_FORMAT_R32G32B32_UINT`|RGB|32|UInt|96-bit|3D indices / data|
|`DXGI_FORMAT_R32G32B32_SINT`|RGB|32|SInt|96-bit|Signed data|
|`DXGI_FORMAT_R16G16B16A16_TYPELESS`|RGBA|16|Typeless|64-bit|HDR targets, compute|
|`DXGI_FORMAT_R16G16B16A16_FLOAT`|RGBA|16|Float|64-bit|HDR rendering|
|`DXGI_FORMAT_R16G16B16A16_UNORM`|RGBA|16|UNORM|64-bit|Color buffer, HDR|
|`DXGI_FORMAT_R16G16B16A16_UINT`|RGBA|16|UInt|64-bit|Structured buffers|
|`DXGI_FORMAT_R16G16B16A16_SNORM`|RGBA|16|SNORM|64-bit|Normal maps|
|`DXGI_FORMAT_R16G16B16A16_SINT`|RGBA|16|SInt|64-bit|Signed integer data|
|`DXGI_FORMAT_R32G32_TYPELESS`|RG|32|Typeless|64-bit|Typed later|
|`DXGI_FORMAT_R32G32_FLOAT`|RG|32|Float|64-bit|Position, velocity|
|`DXGI_FORMAT_R32G32_UINT`|RG|32|UInt|64-bit|Integer data|
|`DXGI_FORMAT_R32G32_SINT`|RG|32|SInt|64-bit|Signed data|
|`DXGI_FORMAT_R32_TYPELESS`|R|32|Typeless|32-bit|Typed later|
|`DXGI_FORMAT_D32_FLOAT`|Depth|32|Float|32-bit|Depth buffer|
|`DXGI_FORMAT_R32_FLOAT`|R|32|Float|32-bit|Scalar, depth|
|`DXGI_FORMAT_R32_UINT`|R|32|UInt|32-bit|Single integer|
|`DXGI_FORMAT_R32_SINT`|R|32|SInt|32-bit|Single signed integer|
|`DXGI_FORMAT_R24G8_TYPELESS`|RG|24+8|Typeless|32-bit|Depth/stencil|
|`DXGI_FORMAT_D24_UNORM_S8_UINT`|Depth+Stencil|24+8|UNORM+UInt|32-bit|Standard depth/stencil|
|`DXGI_FORMAT_R24_UNORM_X8_TYPELESS`|R+X|24+8|Typeless|32-bit|Depth-only storage|
|`DXGI_FORMAT_X24_TYPELESS_G8_UINT`|X+G|24+8|Typeless|32-bit|Stencil-only view|
|`DXGI_FORMAT_R16G16_TYPELESS`|RG|16|Typeless|32-bit|Typed later|
|`DXGI_FORMAT_R16G16_FLOAT`|RG|16|Float|32-bit|Intermediate buffers|
|`DXGI_FORMAT_R16G16_UNORM`|RG|16|UNORM|32-bit|HDR or color buffers|
|`DXGI_FORMAT_R16G16_UINT`|RG|16|UInt|32-bit|Integer buffers|
|`DXGI_FORMAT_R16G16_SNORM`|RG|16|SNORM|32-bit|Normal maps|
|`DXGI_FORMAT_R16G16_SINT`|RG|16|SInt|32-bit|Signed integer|
|`DXGI_FORMAT_R32G8X24_TYPELESS`|RG|32+8+24|Typeless|64-bit|Depth + stencil|
|`DXGI_FORMAT_D32_FLOAT_S8X24_UINT`|Depth+Stencil|32+8+24|Float+UInt|64-bit|Depth/stencil buffer|
|`DXGI_FORMAT_R10G10B10A2_TYPELESS`|RGBA|10+10+10+2|Typeless|32-bit|HDR / compact storage|
|`DXGI_FORMAT_R10G10B10A2_UNORM`|RGBA|10+10+10+2|UNORM|32-bit|HDR with small memory|
|`DXGI_FORMAT_R10G10B10A2_UINT`|RGBA|10+10+10+2|UInt|32-bit|Integer packing|
|`DXGI_FORMAT_R11G11B10_FLOAT`|RGB|11+11+10|Float|32-bit|HDR rendering|
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|RGBA|8|Typeless|32-bit|Typed later|
|`DXGI_FORMAT_R8G8B8A8_UNORM`|RGBA|8|UNORM|32-bit|Standard color texture|
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|RGBA|8|UNORM|32-bit|sRGB display texture|
|`DXGI_FORMAT_R8G8B8A8_UINT`|RGBA|8|UInt|32-bit|Integer buffers|
|`DXGI_FORMAT_R8G8B8A8_SNORM`|RGBA|8|SNORM|32-bit|Normal maps|
|`DXGI_FORMAT_R8G8B8A8_SINT`|RGBA|8|SInt|32-bit|Signed data|
|`DXGI_FORMAT_R16_TYPELESS`|R|16|Typeless|16-bit|Typed later|
|`DXGI_FORMAT_R16_FLOAT`|R|16|Float|16-bit|Scalar float|
|`DXGI_FORMAT_D16_UNORM`|Depth|16|UNORM|16-bit|Depth buffer|
|`DXGI_FORMAT_R16_UNORM`|R|16|UNORM|16-bit|Grayscale or HDR|
|`DXGI_FORMAT_R16_UINT`|R|16|UInt|16-bit|Integer data|
|`DXGI_FORMAT_R16_SNORM`|R|16|SNORM|16-bit|Signed scalar|
|`DXGI_FORMAT_R16_SINT`|R|16|SInt|16-bit|Signed integer|
|`DXGI_FORMAT_R8_TYPELESS`|R|8|Typeless|8-bit|Typed later|
|`DXGI_FORMAT_R8_UNORM`|R|8|UNORM|8-bit|Grayscale|
|`DXGI_FORMAT_R8_UINT`|R|8|UInt|8-bit|Integer data|
|`DXGI_FORMAT_R8_SNORM`|R|8|SNORM|8-bit|Signed scalar|
|`DXGI_FORMAT_R8_SINT`|R|8|SInt|8-bit|Signed integer|
|`DXGI_FORMAT_A8_UNORM`|A|8|UNORM|8-bit|Alpha only|
|`DXGI_FORMAT_R1_UNORM`|R|1|UNORM|1-bit|Masks / stencil|
|`DXGI_FORMAT_BC1_TYPELESS`|RGBA|4:4:4 compressed|Typeless|64 bits / 4x4 block|Diffuse / color compression|
|`DXGI_FORMAT_BC1_UNORM`|RGBA|4:4:4 compressed|UNORM|64 bits / 4x4 block|Diffuse textures|
|`DXGI_FORMAT_BC1_UNORM_SRGB`|RGBA|4:4:4 compressed|UNORM|64 bits / 4x4 block|sRGB textures|
|`DXGI_FORMAT_BC2_TYPELESS`|RGBA|4:4:4+alpha|Typeless|128 bits / 4x4 block|Diffuse + alpha|
|`DXGI_FORMAT_BC2_UNORM`|RGBA|4:4:4+alpha|UNORM|128 bits / 4x4 block|Diffuse + alpha|
|`DXGI_FORMAT_BC2_UNORM_SRGB`|RGBA|4:4:4+alpha|UNORM|128 bits / 4x4 block|sRGB textures|
|`DXGI_FORMAT_BC3_TYPELESS`|RGBA|4:4:4+alpha|Typeless|128 bits / 4x4 block|Diffuse + alpha|
|`DXGI_FORMAT_BC3_UNORM`|RGBA|4:4:4+alpha|UNORM|128 bits / 4x4 block|Diffuse + alpha|
|`DXGI_FORMAT_BC3_UNORM_SRGB`|RGBA|4:4:4+alpha|UNORM|128 bits / 4x4 block|sRGB textures|
|`DXGI_FORMAT_BC4_TYPELESS`|R|1-channel compressed|Typeless|64 bits / 4x4 block|Red-channel textures|
|`DXGI_FORMAT_BC4_UNORM`|R|1-channel compressed|UNORM|64 bits / 4x4 block|Single channel|
|`DXGI_FORMAT_BC4_SNORM`|R|1-channel compressed|SNORM|64 bits / 4x4 block|Normal maps|
|`DXGI_FORMAT_BC5_TYPELESS`|RG|2-channel compressed|Typeless|128 bits / 4x4 block|Normal maps|
|`DXGI_FORMAT_BC5_UNORM`|RG|2-channel compressed|UNORM|128 bits / 4x4 block|Normal maps|
|`DXGI_FORMAT_BC5_SNORM`|RG|2-channel compressed|SNORM|128 bits / 4x4 block|Normal maps|
|`DXGI_FORMAT_B5G6R5_UNORM`|RGB|5/6/5|UNORM|16-bit|Legacy color formats|
|`DXGI_FORMAT_B5G5R5A1_UNORM`|RGBA|5/5/5/1|UNORM|16-bit|Legacy color formats|
|`DXGI_FORMAT_B8G8R8A8_UNORM`|RGBA|8|UNORM|32-bit|Color buffer|
|`DXGI_FORMAT_B8G8R8X8_UNORM`|RGB|8|UNORM|32-bit|Color buffer without alpha|
|`DXGI_FORMAT_R9G9B9E5_SHAREDEXP`|RGB+exp|9+9+9+5|Shared exponent|32-bit|HDR compact|

</details>
