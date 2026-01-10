# D3D12_DESCRIPTOR_HEAP_DESC

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
