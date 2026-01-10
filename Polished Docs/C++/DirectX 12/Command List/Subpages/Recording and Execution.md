# Command List Recording and Execution

1.  **Creation**: Create a `ID3D12GraphicsCommandList` using `ID3D12Device::CreateCommandList()`.
2.  **Recording**: Call `Reset()` on the command list to put it in a recording state. Issue rendering commands (e.g., `DrawInstanced`, `Dispatch`).
3.  **Closing**: Call `Close()` to finalize the recording.
4.  **Execution**: Submit the command list to a [[Command Queue]] via `ExecuteCommandLists()`.

Once a command list is submitted, it can be reset and reused to record a new set of commands, which helps minimize allocations.
