# Root Signature Creation

Root signatures can be defined in two ways:

1.  **In C++ code**: By populating a `D3D12_ROOT_SIGNATURE_DESC` structure and serializing it.
2.  **In HLSL**: By using the `[RootSignature("...")]` syntax directly in a shader file. This is often preferred as it keeps the binding logic co-located with the shader code.

Regardless of the method, the final serialized signature is used to create a `ID3D12RootSignature` object, which is then bound to the pipeline before draw calls.
