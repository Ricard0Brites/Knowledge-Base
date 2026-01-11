
---
# DirectX 12 Command Recording & Reuse Workflow

```table-of-contents
```

This document outlines the best practices for recording and reusing command lists in DirectX 12 to minimize CPU overhead.

---

## 1. Precomputation vs. Runtime Generation

A key aspect of DirectX 12 is understanding what can be precomputed offline versus what must be generated at runtime.

### What Cannot Be Precomputed

-   **[[Command List]]s and [[Bundle]]s**: These contain raw GPU commands and are tied to a specific GPU driver, device, and memory layout. They are not serializable and must be recorded at runtime.

### What Can Be Precomputed

-   **Shader Bytecode (DXIL)**: Compile HLSL to `.dxil` during your build process to avoid expensive runtime shader compilation.
-   **[[Root Signature]]s**: These are fully deterministic and can be serialized offline. They are cheap to create at runtime.
-   **[[Pipeline State Object]]s**: PSOs encapsulate shaders, input layouts, and various states. Define their layouts offline and create them at startup.

---

## 2. The Rendering Workflow

### 2.1 Runtime Initialization (Once per run)

At application startup, create GPU state objects like [[Root Signature]]s, [[Pipeline State Object]]s, and [[Descriptor Heap]]s. Upload static resources such as vertex/index buffers and textures that won't change per frame.

### 2.2 Recording Bundles (Once at runtime)

A **[[Bundle]]** is a reusable command list that records rendering commands for static geometry. It's ideal for objects like foliage, static meshes, or particles with a fixed topology.

-   **What a Bundle Records**: `[[Vertex Buffer View (VBV)|IASetVertexBuffers]]`, `[[Index Buffer View (IBV)|IASetIndexBuffer]]`, **Draw*** calls.
-   **What a Bundle Does NOT Record**: Per-object transforms or any other dynamic data.

### 2.3 The Frame Loop (Every frame)

-   **Update Dynamic Data**: The only per-frame CPU cost should be updating dynamic data like [[Constant Buffer View (CBV)]]s, structured buffers for instance data, and descriptor tables.
-   **Execute Bundles**: Use **ExecuteBundle** to replay the pre-recorded drawing commands. The bundle provides *how* to draw, while the dynamic data (like [[Constant Buffer View (CBV)]]s) provides the *where* and *how* it is drawn for that frame.

---

## 3. Static vs. Dynamic Responsibilities

| Responsibility          | Where                  |
| ----------------------- | ---------------------- |
| Geometry Topology       | [[Bundle]]             |
| Draw Call Structure     | [[Bundle]]             |
| Shaders / Coloring      | [[Pipeline State Object]]                |
| Object Transforms       | [[Constant Buffer View (CBV)]]/Structured Buffer |
| Material Parameters     | [[Constant Buffer View (CBV)]]/[[Shader Resource View (SRV)]]        |
| Output Targets          | [[Render Target View (RTV)]]/[[Depth Stencil View (DSV)]]        |

---

## 4. Comparison to DirectX 11

-   **DirectX 11**: The driver rebuilds the command stream every frame, leading to high CPU overhead with many objects.
-   **DirectX 12**: The command structure is built once. The CPU only updates memory, and the GPU executes clean, pre-validated command streams.

---

## 5. Key Takeaways

-   You **cannot** ship pre-recorded [[Command List]]s.
-   You **can** ship shader bytecode, [[Root Signature]]s, and [[Pipeline State Object]] definitions.
-   You **should** record [[Bundle]]s once at runtime and reuse them every frame, feeding them dynamic data via [[Constant Buffer View (CBV)]]s. This is the core principle for achieving scalability and low CPU overhead in DirectX 12.
