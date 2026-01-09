---
# Code Structure

The code is organized into a few key functions:

*   `WinMain`: The application's entry point. It handles window creation and the main message loop.
*   `WindowProc`: The window procedure, which handles window messages (like closing the window).
*   `OnInit`: Initializes all the DirectX 12 objects.
*   `OnUpdate`: A placeholder for application logic (currently empty).
*   `OnRender`: Contains the rendering logic that is called every frame.
*   `OnDestroy`: Cleans up resources.
*   `WaitForPreviousFrame`: A helper function for synchronizing the CPU and GPU.
