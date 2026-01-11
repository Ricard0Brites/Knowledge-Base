# Root Signature Overview

The **Root Signature** is a cornerstone of the DirectX 12 binding model. It defines the contract between the application and the shaders, specifying what resources the pipeline can access. It acts as a blueprint for how data like [[Constant Buffer View (CBV)|constant buffers]], [[Shader Resource View (SRV)|textures]], and [[Sampler|samplers]] are mapped to the shader stages.

Before a [[Pipeline State Object]] can be created, the root signature must be defined and finalized.