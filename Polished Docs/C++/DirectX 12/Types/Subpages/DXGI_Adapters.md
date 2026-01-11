
# DXGI Adapter Interfaces

The DXGI Adapter interface represents a display adapter (a physical GPU, or a software-emulated one). It is used to query adapter properties, available outputs (monitors), and video memory information.

## Adapter Versions and Key Features

| Interface       | DXGI Version | Key Feature(s) Introduced                                      |
|-----------------|--------------|----------------------------------------------------------------|
| `IDXGIAdapter`  | 1.0          | Basic adapter enumeration and property queries (`DXGI_ADAPTER_DESC`). |
| `IDXGIAdapter1` | 1.1          | Enumeration of software/headless adapters (`DXGI_ADAPTER_DESC1`). |
| `IDXGIAdapter2` | 1.2          | Queries for graphics and compute preemption granularity (`DXGI_ADAPTER_DESC2`). |
| `IDXGIAdapter3` | 1.4          | Video memory budget and residency queries.                      |
| `IDXGIAdapter4` | 1.6          | Queries for hardware scheduling and cache coherence (`DXGI_ADAPTER_DESC3`). |

---

## Adapter Descriptor Structures

### `DXGI_ADAPTER_DESC` (from `IDXGIAdapter`)

Provides fundamental hardware information.

| Field                   | Description                                    |
|-------------------------|------------------------------------------------|
| `Description`           | A string containing the adapter name.          |
| `VendorId`              | The PCI ID of the hardware vendor.             |
| `DeviceId`              | The PCI ID of the hardware device.             |
| `DedicatedVideoMemory`  | The number of bytes of dedicated video memory. |
| `DedicatedSystemMemory` | The number of bytes of dedicated system memory. |
| `SharedSystemMemory`    | The number of bytes of shared system memory.   |
| `AdapterLuid`           | A locally unique identifier for the adapter.   |

### `DXGI_ADAPTER_DESC1` (from `IDXGIAdapter1`)

Adds flags to identify the adapter type.

| Added Field | Description                                       |
|-------------|---------------------------------------------------|
| `Flags`     | Flags indicating if the adapter is software, remote, etc. |

### `DXGI_ADAPTER_DESC2` (from `IDXGIAdapter2`)

Adds information about preemption capabilities, which is crucial for understanding how the GPU handles task switching.

| Added Field                     | Description                               |
|---------------------------------|-------------------------------------------|
| `GraphicsPreemptionGranularity` | The preemption level for graphics tasks.  |
| `ComputePreemptionGranularity`  | The preemption level for compute tasks.   |

### `DXGI_ADAPTER_DESC3` (from `IDXGIAdapter4`)

Adds flags related to advanced hardware features.

| Added Field | Description                                      |
|-------------|--------------------------------------------------|
| `Flags`     | Flags for hardware scheduling, UMA support, and cache coherence. |

---

## Key Capabilities by Interface

### `IDXGIAdapter3`
- `QueryVideoMemoryInfo`: Get detailed information about local and non-local memory usage and budget.
- `SetVideoMemoryReservation`: Reserve a specific amount of video memory for the application.
- `RegisterVideoMemoryBudgetChangeNotificationEvent`: Register for an event that is signaled when the memory budget changes.

---

## Key Takeaways
- **Adapter Properties**: Use the `GetDesc` methods (`GetDesc`, `GetDesc1`, etc.) on the appropriate interface to get a description of the adapter's capabilities.
- **Memory Management**: `IDXGIAdapter3` is essential for modern applications that need to manage their video memory usage explicitly, which is a core part of DirectX 12.
- **Enumeration**: Adapter interfaces are typically obtained by enumerating them from a DXGI Factory (`IDXGIFactory::EnumAdapters`).
