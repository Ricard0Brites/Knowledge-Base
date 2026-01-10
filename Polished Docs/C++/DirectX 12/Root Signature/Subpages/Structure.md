# Root Signature Structure

A root signature is a collection of **root parameters**, which can be one of three types:

1.  **Root Constants**: A small number of 32-bit values passed directly to shaders. This is the fastest way to get data to the pipeline, but it's limited in size.
2.  **Root Descriptors**: A direct descriptor ([[CBV]], [[SRV]], or [[Unordered Access View (UAV)|UAV]]) stored directly in the root signature. This offers fast access without the indirection of a descriptor table.
3.  **Descriptor Tables**: A pointer to a range within a [[Descriptor Heap]]. This is the most flexible approach, allowing shaders to access a large number of resources.

The entire root signature has a maximum size, so it's a trade-off between the number and type of parameters.
