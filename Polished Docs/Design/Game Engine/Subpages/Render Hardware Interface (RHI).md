---
# Rendering Hardware Interface (RHI)

RHI is an abstraction layer between the engine renderer and the GPU API (D3D12, Vulkan, Metal). It exposes **low-level GPU operations** without knowing rendering concepts like meshes, lights, or volumes.  

## Purpose
- Provides a **universal API wrapper** across different graphics APIs.  
- Centralizes **GPU resource management** (buffers, textures, shaders, pipelines, descriptors, fences, swapchains).  
- Enables **thread-safe command recording** and submission.  
- Ensures **correct API usage** and synchronization.  

## Responsibilities
- Create/Destroy GPU resources:
  - Buffers (vertex, index, constant)  
  - Textures (2D, 3D, cube)  
  - Pipeline State Objects  
  - Descriptors / Descriptor Sets  
- Record GPU commands:
  - Bind pipeline  
  - Bind buffers/textures  
  - Draw / DrawIndexed / Dispatch  
- Submit commands to GPU queues  
- Synchronize execution with fences or events  
- Present frames (swapchain flip)  

## What RHI does NOT handle
- Rendering logic: materials, lighting, visibility, frame graphs  
- High-level objects: meshes, lights, cameras, volumes  
- Scene semantics: shadowing, transparency, volumetrics  

## Renderer → RHI flow
1. Renderer defines high-level objects (Mesh, Light, Volume, Material).  
2. Renderer converts objects into GPU resources and draw/dispatch commands.  
3. Renderer submits commands to RHI.  
4. RHI executes commands on GPU.  
5. RHI calls `Present()` to display the frame.  

### Example: Light
- Engine: `PointLight { position, color, intensity }`  
- Renderer converts: `LightGPU { float3 pos; float intensity; float3 color; }`  
- RHI uploads as constant buffer, binds it, executes draw/dispatch.  
- RHI never knows this is a light.  

## Unreal Engine context
- Renderer builds frame graph: passes, visibility, materials, lights.  
- FRHICommandList records draw commands.  
- RHI executes commands on GPU.  
- `RHIEndDrawingViewport()` internally calls Present.  
- RHI thread may be separate for async GPU submission.  

## Summary of exposed functions
- `CreateBuffer(size, usage, flags)`  
- `CreateTexture(desc)`  
- `CreateShader(compiledBytecode)`  
- `CreatePipelineState(desc)`  
- `BeginCommandList() / EndCommandList()`  
- `BindPipeline(...) / BindBuffer(...) / BindTexture(...)`  
- `Draw / DrawIndexed / Dispatch`  
- `SignalFence / WaitFence`  
- `Present(swapchain, flags)`