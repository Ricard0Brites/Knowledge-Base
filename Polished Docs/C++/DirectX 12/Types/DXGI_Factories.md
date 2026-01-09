
# DXGI Factory Interfaces

The DXGI (DirectX Graphics Infrastructure) factory is the entry point for creating DXGI objects, primarily for enumerating graphics adapters and creating swap chains. The interface has been versioned over time to add new capabilities.


## Factory Versions and Key Features

| Interface         | DXGI Version | Key Feature(s) Introduced                                   |
|-------------------|--------------|-------------------------------------------------------------|
| `IDXGIFactory`    | 1.0          | Base adapter enumeration and legacy swap chain creation.    |
| `IDXGIFactory1`   | 1.1          | Enumeration of software adapters.                           |
| `IDXGIFactory2`   | 1.2          | **Flip-model swap chains** (`CreateSwapChainForHwnd`).      |
| `IDXGIFactory3`   | 1.3          | Adapter lookup by Locally Unique Identifier (LUID).         |
| `IDXGIFactory4`   | 1.4          | Explicit enumeration of the WARP (software) adapter.        |
| `IDXGIFactory5`   | 1.5          | Feature queries for HDR and color spaces; waitable swap chains. |
| `IDXGIFactory6`   | 1.6          | **GPU preference enumeration** (high-performance vs. power-saving). |
| `IDXGIFactory7`   | 1.7          | Notifications for adapter arrival/removal (hot-plugging).   |

---

## Capabilities by Interface (Cumulative)

### `IDXGIFactory` (Base)
- `EnumAdapters`: Enumerate adapters connected to a display output.
- `CreateSwapChain`: Create legacy, bitblt-style swap chains.
- `MakeWindowAssociation`: Control windowed vs. fullscreen behavior.

### `IDXGIFactory1`
- `EnumAdapters1`: Enumerate all adapters, including software and headless ones.

### `IDXGIFactory2`
- `CreateSwapChainForHwnd`: Create modern, more efficient flip-model swap chains for a window handle.
- `CreateSwapChainForCoreWindow`: For UWP applications.
- `CreateSwapChainForComposition`: For use with the DirectComposition API.

### `IDXGIFactory4`
- `EnumWarpAdapter`: Get a reference to the WARP (Windows Advanced Rasterization Platform) software adapter.

### `IDXGIFactory6`
- `EnumAdapterByGpuPreference`: Allows requesting an adapter based on a performance preference (`DXGI_GPU_PREFERENCE_HIGH_PERFORMANCE` or `DXGI_GPU_PREFERENCE_MINIMUM_POWER`).

### `IDXGIFactory7`
- `RegisterAdaptersChangedEvent`: Register for an event that is signaled when graphics adapters are added or removed.

---

## Key Takeaways
- **Modern Development**: Modern DirectX 12 applications should use `IDXGIFactory6` or newer to correctly handle systems with multiple GPUs (e.g., laptops with integrated and discrete graphics).
- **Flip-Model Swap Chains**: `IDXGIFactory2` is the minimum required for creating efficient flip-model swap chains, which are the standard for modern graphics applications.
- **Purpose**: Factories are responsible for adapter discovery and swap chain creation, not for querying GPU features (which is done via `ID3D12Device::CheckFeatureSupport`).
