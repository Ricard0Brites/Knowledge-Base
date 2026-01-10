---
# Render Target View (RTV)

A Render Target View (RTV) specifies a resource that the GPU can write to at the end of a render pass. It acts as a descriptor for a render target.

## Concept

- **Render targets (RTs)** are **GPU buffers where pixel data is written during a render pass**.
- While materials define *what* is written (color, normal, etc.), they do **not** create render targets for each object. Instead, all objects in a scene typically render their data into a shared set of render targets.
- The **swap chain back buffer** is the final render target that holds the composited image presented to the screen.

---

## Graphics Pipeline Flow

The following diagram illustrates how render targets fit into the rendering pipeline:

```
Objects & Materials
        │
        ▼
+-----------------+
| Render Targets  |  ← Each RT stores one type of data (e.g., color, normal, etc.)
+-----------------+
        │
        ▼
+-----------------+
| Post-processing |  ← Combines RTs, applies effects like lighting and bloom.
+-----------------+
        │
        ▼
+-----------------+
| Swap Chain      |  ← Presents the final image to the user.
+-----------------+
```

---

### Example

Imagine a scene full of pens, where each pen's material outputs three pieces of information: **color**, **normal**, and **transparency**.

For this entire scene, the engine would create **three render targets**:

| Render Target | Stores                               |
|---------------|--------------------------------------|
| RT0           | The **Color** (albedo) of all pens   |
| RT1           | The **Normals** of all pens          |
| RT2           | The **Transparency** of all pens     |

All pens write their pixel data into this same set of render targets. After all objects are drawn, post-processing effects (like lighting) are applied by reading from these render targets. Finally, the result is resolved into the **swap chain's back buffer**, which is what the user sees on screen.