# Pipeline State Object Overview

A **Pipeline State Object (PSO)** is a fundamental concept in DirectX 12 that unifies a large portion of the graphics pipeline into a single, immutable object. In older APIs like DirectX 11, states like shaders, blend settings, and rasterizer configurations were set independently, leading to significant CPU overhead.

By consolidating these into one object, DirectX 12 allows the driver to pre-compile and validate the entire pipeline state upfront. This dramatically reduces the work needed during a draw call, enabling much higher performance and more draw calls per frame.
