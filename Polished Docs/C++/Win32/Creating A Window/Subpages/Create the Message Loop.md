---
# Step 10: Create the Message Loop

```cpp
MSG msg = {};
while (GetMessage(&msg, nullptr, 0, 0))
{
    TranslateMessage(&msg);
    DispatchMessage(&msg);
}
```

### What it does

Processes OS messages until the application exits.

### Why it is required

Without a message loop:

- The window freezes
- Windows marks the app as unresponsive

This loop is mandatory for all Win32 applications.