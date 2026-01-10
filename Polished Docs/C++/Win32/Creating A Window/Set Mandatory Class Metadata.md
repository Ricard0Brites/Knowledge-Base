---
# Step 6: Set Mandatory Class Metadata

```cpp
wc.cbSize = sizeof(WNDCLASSEX);
wc.lpszClassName = L"MyWindowClass";
```

### What it does

- `cbSize`: versioning and validation
- `lpszClassName`: unique identifier for the class

### Why it is required

Windows must know:

- Which structure layout you are using
- How to refer to this class later