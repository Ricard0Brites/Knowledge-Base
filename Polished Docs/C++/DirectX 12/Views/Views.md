# Views

In DirectX 12, a "view" is a specific interpretation of resource data. It allows the GPU to understand how to access and use the data stored in a resource, such as a texture or a buffer, in a particular format.

For example, a [[Constant Buffer View (CBV)]] tells the GPU to treat a piece of memory as a constant buffer.

## Types of Views

Here are the most common types of views in DirectX 12:

- [[Constant Buffer View (CBV)]]
- [[Vertex Buffer View (VBV)]]
- [[Index Buffer View (IBV)]]
- [[Shader Resource View (SRV)]]
- [[Unordered Access View (UAV)]]
- [[Sampler]]
- [[Render Target View (RTV)]]
- [[Depth Stencil View (DSV)]]
- [[Stream Output View (SOV)]]
- [[Rasterizer Ordered View (ROV)]]