---
# OnRender() - The Rendering Loop

This function is called every frame to render the triangle.

1.  **Reset Command List and Allocator**: The command allocator and command list are reset to be reused for the new frame.
2.  **Set Pipeline State**: The root signature and PSO are bound to the command list.
3.  **Set Viewport and Scissor Rect**: These define the area of the render target to draw to.
4.  **Resource Barrier**: A resource barrier is used to transition the current back buffer from the "present" state to the "render target" state.
5.  **Set Render Target**: `OMSetRenderTargets` sets the current back buffer as the active render target.
6.  **Clear Render Target**: `ClearRenderTargetView` clears the back buffer to a solid color.
7.  **Draw**:
    - `IASetPrimitiveTopology` tells the GPU to interpret the vertex data as a triangle list.
    - `IASetVertexBuffers` binds our vertex buffer.
    - `DrawInstanced` issues the draw call to render the 3 vertices of our triangle.
8.  **Resource Barrier (Present)**: Another resource barrier transitions the back buffer back to the "present" state, ready to be shown on the screen.
9.  **Execute Command List**: The command list is closed and then executed on the command queue.
10. **Present Frame**: `m_swapChain->Present(1, 0)` tells the swap chain to present the back buffer to the screen.
11. **Wait**: `WaitForPreviousFrame()` is called to synchronize with the GPU.