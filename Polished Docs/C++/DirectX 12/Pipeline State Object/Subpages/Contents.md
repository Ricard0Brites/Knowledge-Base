# What a PSO Contains

A PSO encapsulates most of the GPU's state, including:

-   **[[Root Signature]]**: Defines the resources the pipeline will access.
-   **Shaders**: Bytecode for the Vertex, Pixel, Geometry, Hull, and Domain shaders.
-   **Input Layout**: The format of the vertex data.
-   **Primitive Topology Type**: How vertices are interpreted (e.g., as triangles, lines).
-   **Blend State**: How pixels are blended with the render target.
-   **Rasterizer State**: Culling, fill mode, etc.
-   **Depth-Stencil State**: Settings for depth and stencil tests.
-   **Render Target Formats**: The format of the output textures.
