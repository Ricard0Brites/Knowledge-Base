```table-of-contents
```

The `D3D12_COMMAND_LIST_TYPE` enum defines the purpose of a [[Command List|command list]], determining which commands are valid and how GPU state is managed.

---

## Command List Types

| Type | Value | Purpose & Allowed Commands | State Inheritance | Use Case |
|---|---|---|---|---|
| `DIRECT` | 0 | General-purpose: draw, compute, copy, etc. | None | Main rendering commands. |
| `BUNDLE` | 1 | Secondary list executed by a `DIRECT` list. | Inherits all state except PSO and primitive topology. | Reusing common command sequences (e.g., static geometry). |
| `COMPUTE` | 2 | Compute shaders (`Dispatch`). No draw calls. | None | GPU-based calculations not tied to rendering. |
| `COPY` | 3 | Resource copies (`CopyResource`, etc.). No draw/dispatch. | None | Asynchronous data transfers. |
| `VIDEO_DECODE` | 4 | Hardware-accelerated video decoding. | N/A | Video playback. |
| `VIDEO_PROCESS` | 5 | Video processing (color conversion, filters). | N/A | Real-time video effects. |
| `VIDEO_ENCODE` | 6 | Hardware-accelerated video encoding. | N/A | Video capture/streaming. |
| `NONE` | - | Invalid type. | N/A | Reserved. |

## Key Rules

*   **Queue Affinity**: A command list's type must match the [[Command Queue|command queue]] it's executed on.
*   **State Inheritance**:
    *   **Direct Lists**: Start with default state. All required states must be set explicitly.
    *   **Bundles**: Inherit most state from the parent direct list, reducing redundant state changes.
