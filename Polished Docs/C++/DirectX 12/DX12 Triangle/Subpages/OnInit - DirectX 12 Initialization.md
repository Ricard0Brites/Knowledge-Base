---
# OnInit() - DirectX 12 Initialization

This is the most complex part of the code. It sets up all the necessary DirectX 12 objects in the correct order.

1.  **Enable Debug Layer**:
    - Wrapped in an `#if defined(_DEBUG)` block, this code enables extra debugging information from the DirectX 12 runtime, which is very useful during development.
2.  **Device Creation**:
    - A `DXGIFactory` is created to enumerate graphics adapters.
    - `D3D12CreateDevice` creates the main `ID3D12Device` object, which represents the GPU.
3.  **Command Queue**:
    - An `ID3D12CommandQueue` is created. This is where the CPU submits command lists to be executed by the GPU.
4.  **Swap Chain**:
    - An `IDXGISwapChain` is created. The swap chain manages the back buffers that are rendered to and then "swapped" to be presented on the screen. This example uses two back buffers for smooth rendering.
5.  **Descriptor Heaps and Render Target Views (RTVs)**:
    - A descriptor heap for Render Target Views (`RTVs`) is created.
    - An RTV is created for each back buffer in the swap chain. The RTV describes the buffer as a render target to the GPU.
6.  **Command Allocator**:
    - An `ID3D12CommandAllocator` is created. This object manages the memory for command lists.
7.  **Root Signature**:
    - A root signature defines the resources that the shaders will use. In this simple example, we use an empty root signature, but we still need to create it.
8.  **Shaders and Pipeline State Object (PSO)**:
    - The vertex and pixel shaders are compiled from HLSL source code embedded as a string in the C++ file.
    - **Vertex Shader (`VSMain`)**: Takes a position and a color as input and passes them through to the pixel shader.
    - **Pixel Shader (`PSMain`)**: Takes the interpolated color from the vertex shader and outputs it as the final pixel color.
    - An `ID3D12PipelineState` (PSO) is created. The PSO is a large object that encapsulates most of the GPU's state, including the shaders, input layout, rasterizer state, and more. Creating PSOs is expensive, so it's done during initialization.
9.  **Command List**:
    - An `ID3D12GraphicsCommandList` is created. This is where we will record the drawing commands. It's initially created in a "closed" state.
10. **Vertex Buffer**:
    - The vertices of the triangle are defined in a `Vertex` struct array. Each vertex has a position and a color.
    - An `ID3D12Resource` (the vertex buffer) is created in GPU memory, and the vertex data is copied into it.
11. **Synchronization (Fences)**:
    - An `ID3D12Fence` and an event handle are created to synchronize the CPU and GPU. This is necessary to ensure that the CPU doesn't get too far ahead of the GPU.