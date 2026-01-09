---
# Step 9: Show the Window

```cpp
ShowWindow(hwnd, SW_SHOW);
UpdateWindow(hwnd);
```

### What it does

- Makes the window visible
- Forces an initial paint

### Why it is required

Windows creates windows hidden by default.

Until shown:

- The user sees nothing
- No rendering is visible