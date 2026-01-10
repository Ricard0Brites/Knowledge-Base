# PSO Creation and Usage

PSOs are typically created at initialization time by filling out a `D3D12_GRAPHICS_PIPELINE_STATE_DESC` structure and calling `ID3D12Device::CreateGraphicsPipelineState`.

Once created, a PSO is immutable. To change the pipeline configuration, you don't modify the PSO; you bind a *different* PSO to the [[Command List]]. Because they are pre-compiled, switching between PSOs is an extremely fast operation.
