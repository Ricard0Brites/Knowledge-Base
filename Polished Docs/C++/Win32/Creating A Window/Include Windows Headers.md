---
# Step 1: Include Windows Headers

```cpp
#include <windows.h>
```

### What it does

Provides access to the Win32 API:

- Window creation
- Message handling
- OS-level types (HWND, MSG, etc.)

### Why it is required

Win32 is a C API exposed through this header. Without it, none of the windowing or message functions exist.