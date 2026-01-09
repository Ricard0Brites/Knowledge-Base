---
# Step 5: Assign the Application Instance

```cpp
wc.hInstance = GetModuleHandle(nullptr);
```

### What it does

Identifies which executable or DLL owns the window class.

### Why it is required

Windows uses this handle internally to:

- Resolve resources
- Track ownership