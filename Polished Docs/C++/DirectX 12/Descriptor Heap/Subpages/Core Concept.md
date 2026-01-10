# Descriptor Heap Core Concept

The mental model for D3D12 resource binding is:
1.  **Resource**: Raw GPU memory (e.g., a texture).
2.  **Descriptor**: Metadata describing the resource (e.g., its format, dimensions).
3.  **Descriptor Heap**: An array of descriptors.
4.  **Root Signature**: Defines how descriptor tables are mapped to shader registers, allowing shaders to find and use the correct descriptors.
