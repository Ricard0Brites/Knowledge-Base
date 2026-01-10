# D3D12_DESCRIPTOR_HEAP_TYPE

This enum specifies the type of descriptors a heap can contain. A heap can only store one type of descriptor.

| Type | Shader-Visible | Purpose |
|---|---|---|
| `CBV_SRV_UAV` | Yes | Stores [[#CBV — Constant Buffer View|CBVs]], [[#SRV — Shader Resource View|SRVs]], and [[#UAV — Unordered Access View|UAVs]] for general-purpose resource binding. |
| `SAMPLER` | Yes | Stores [[Sampler|sampler descriptors]] for texture sampling. |
| `RTV` | No | Stores [[Render Target View|Render Target Views (RTVs)]] for render pass outputs. |
| `DSV` | No | Stores [[Depth Stencil View|Depth Stencil Views (DSVs)]] for depth/stencil testing. |
