```table-of-contents
```

A **descriptor heap** is a memory array of [[Descriptor|descriptors]], which are small blocks of data that describe a resource to the GPU. In D3D12, the application must explicitly manage these heaps to bind resources like buffers, textures, and samplers to the shader pipeline.

---

## `D3D12_DESCRIPTOR_HEAP_TYPE`

This enum specifies the type of descriptors a heap can contain. A heap can only store one type of descriptor.

| Type | Shader-Visible | Purpose |
|---|---|---|
| `CBV_SRV_UAV` | Yes | Stores [[#CBV — Constant Buffer View|CBVs]], [[#SRV — Shader Resource View|SRVs]], and [[#UAV — Unordered Access View|UAVs]] for general-purpose resource binding. |
| `SAMPLER` | Yes | Stores [[Sampler|sampler descriptors]] for texture sampling. |
| `RTV` | No | Stores [[Render Target View|Render Target Views (RTVs)]] for render pass outputs. |
| `DSV` | No | Stores [[Depth Stencil View|Depth Stencil Views (DSVs)]] for depth/stencil testing. |

---

## Descriptor Types

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

---

## `D3D12_DESCRIPTOR_HEAP_DESC`

This structure is used to create a descriptor heap.

```cpp
D3D12_DESCRIPTOR_HEAP_DESC desc = {};
desc.Type           = D3D12_DESCRIPTOR_HEAP_TYPE_CBV_SRV_UAV;
desc.NumDescriptors = 1024;
desc.Flags          = D3D12_DESCRIPTOR_HEAP_FLAG_SHADER_VISIBLE;
desc.NodeMask       = 0;
```

*   **`Type`**: The `D3D12_DESCRIPTOR_HEAP_TYPE` of the heap.
*   **`NumDescriptors`**: The number of descriptors the heap will contain.
*   **`Flags`**:
    *   `D3D12_DESCRIPTOR_HEAP_FLAG_SHADER_VISIBLE`: The heap is accessible by shaders.
    *   `D3D12_DESCRIPTOR_HEAP_FLAG_NONE`: The heap is CPU-only, used for staging descriptors before copying them to a shader-visible heap.
*   **`NodeMask`**: For multi-adapter systems (usually 0).

---

## Core Concept

The mental model for D3D12 resource binding is:
1.  **Resource**: Raw GPU memory (e.g., a texture).
2.  **Descriptor**: Metadata describing the resource (e.g., its format, dimensions).
3.  **Descriptor Heap**: An array of descriptors.
4.  **Root Signature**: Defines how descriptor tables are mapped to shader registers, allowing shaders to find and use the correct descriptors.
