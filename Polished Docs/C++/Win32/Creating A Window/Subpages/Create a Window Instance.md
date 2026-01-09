---
# Step 8: Create a Window Instance

```cpp
HWND hwnd = CreateWindowEx(
    0,
    L"MyWindowClass",
    L"Window Title",
    WS_OVERLAPPEDWINDOW,
    CW_USEDEFAULT, CW_USEDEFAULT,
    width, height,
    nullptr, nullptr,
    hInstance,
    nullptr
);
```

### What it does

Creates an actual window on screen.

### Why it is required

The window class only defines behavior.

This call creates:

- A real OS window
- A unique HWND handle

All rendering and input target this handle.