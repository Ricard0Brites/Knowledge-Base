---
# WinMain

This is the standard entry point for a Windows application.

- It first registers a window class (`WNDCLASSEX`).
- Then it creates the main application window using `CreateWindow`.
- It calls `OnInit()` to set up DirectX 12.
- Finally, it enters a `while` loop that processes window messages and calls `OnUpdate()` and `OnRender()` repeatedly until the user closes the window.