---
# How to Compile and Run

This code is a single file and is intended to be compiled as a Windows application. To compile it, you would typically use Visual Studio with the "Desktop development with C++" workload installed. You will also need the Windows SDK.

1.  Create a new C++ project in Visual Studio.
2.  Add this `DX12Triangle.cpp` file to the project.
3.  In the project properties, under "Linker" -> "Input", add `d3d12.lib`, `dxgi.lib`, and `d3dcompiler.lib` to the "Additional Dependencies".
4.  Build and run the project. You should see a window with a colored triangle on a blue background.