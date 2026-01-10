D3D12_DESCRIPTOR_HEAP_DESC

## One-sentence summary

A descriptor heap is a GPU-accessible table of resource descriptors that D3D12 requires to explicitly bind buffers, textures, and samplers to shaders.

## What is a descriptor heap?

A **descriptor heap** is a GPU-visible array that stores **descriptors**.  
A **descriptor** is a small structure that describes how the GPU should access a resource (buffer, texture, sampler), not the resource itself.

Examples of what a descriptor can represent:

- Constant Buffer View (CBV)
    
- Shader Resource View (SRV)
    
- Unordered Access View (UAV)
    
- Sampler
    

---

## What is it used for?

Descriptor heaps are used to **bind resources to shaders**.

In D3D12, shaders do not bind resources directly. Instead:

1. Resources are described by descriptors
    
2. Descriptors live inside descriptor heaps
    
3. Shaders access descriptors via indices or tables defined in the root signature
    

This enables:

- Explicit control over GPU memory
    
- Low-overhead resource binding
    
- Efficient batching and reuse of bindings
    

---

## Why do you need it?

D3D12 removed implicit driver-managed binding (from D3D11).  
You **must** manage resource binding explicitly.

You need descriptor heaps because:

- The GPU can only access resources through descriptors
    
- Root signatures reference descriptor tables, not raw resources
    
- GPU-visible descriptor heaps are required for shader access
    
- CPU-only heaps are required for staging and descriptor creation
    

Without descriptor heaps, shaders cannot see textures, buffers, or samplers.

---

## All `D3D12_DESCRIPTOR_HEAP_TYPE` values

|Enum Value|Numeric|Purpose|Typical Descriptors Stored|Shader Visible|
|---|---|---|---|---|
|`D3D12_DESCRIPTOR_HEAP_TYPE_CBV_SRV_UAV`|`0`|General resource access|CBV, SRV, UAV|**Yes**|
|`D3D12_DESCRIPTOR_HEAP_TYPE_SAMPLER`|`1`|Sampler state binding|Sampler descriptors|**Yes**|
|`D3D12_DESCRIPTOR_HEAP_TYPE_RTV`|`2`|Render target outputs|Render Target Views|**No**|
|`D3D12_DESCRIPTOR_HEAP_TYPE_DSV`|`3`|Depth/stencil outputs|Depth Stencil Views|**No**|
|`D3D12_DESCRIPTOR_HEAP_TYPE_NUM_TYPES`|`4`|Enum sentinel|Not a real heap|N/A|

### CBV, SRV, UAV — meanings and roles

#### CBV — Constant Buffer View

- **Stands for:** Constant Buffer View
    
- **Purpose:** Read-only shader constants (uniform data)
    
- **Typical data:** Per-frame, per-object, per-material parameters
    
- **Shader access:** Read-only
    
- **Backed by:** `ID3D12Resource` created as a buffer
    
- **Constraints:**
    
    - Must be 256-byte aligned
        
    - Limited size (64 KB per CBV)
        

---

#### SRV — Shader Resource View

- **Stands for:** Shader Resource View
    
- **Purpose:** Read-only access to resources
    
- **Typical data:**
    
    - Textures (2D, 3D, cube)
        
    - Structured buffers
        
    - Typed buffers
        
- **Shader access:** Read-only
    
- **Backed by:** Textures or buffers
    
- **Common uses:** Textures, lookup tables, static data
    

---

#### UAV — Unordered Access View

- **Stands for:** Unordered Access View
    
- **Purpose:** Read–write shader access
    
- **Typical data:**
    
    - RW textures
        
    - RW structured buffers
        
    - Append/consume buffers
        
- **Shader access:** Read + write
    
- **Pipeline stages:** Compute, pixel, mesh, amplification (and others)
    
- **Supports:** Atomic operations
    
![[Pasted image 20260110173049.png]]
---

### Comparison table

|View|Read|Write|Typical Use|
|---|---|---|---|
|CBV|Yes|No|Small constant data|
|SRV|Yes|No|Textures, read-only buffers|
|UAV|Yes|Yes|Compute outputs, RW textures|
---

## `D3D12_DESCRIPTOR_HEAP_DESC`

Defines how a descriptor heap is created.

`D3D12_DESCRIPTOR_HEAP_DESC desc = {}; desc.Type = D3D12_DESCRIPTOR_HEAP_TYPE_CBV_SRV_UAV; desc.NumDescriptors = 1024; desc.Flags = D3D12_DESCRIPTOR_HEAP_FLAG_SHADER_VISIBLE; desc.NodeMask = 0;`

### Fields

- **Type**  
    Which kind of descriptors the heap stores.
    
- **NumDescriptors**  
    Total number of descriptors allocated in the heap.
    
- **Flags**
    
    - `SHADER_VISIBLE`: required if shaders access it
        
    - `NONE`: CPU-only heap
        
- **NodeMask**  
    Multi-adapter support (usually `0`).
    

---

## Key mental model

- **Resource** → actual GPU memory
    
- **Descriptor** → description of how to access that memory
    
- **Descriptor Heap** → array of descriptors
    
- **Root Signature** → tells shaders where descriptors live