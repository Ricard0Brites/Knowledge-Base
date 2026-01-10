---
# Step 3: Define a Window Class

```cpp
WNDCLASSEX wc = {};
```

### What it does

Describes **how windows of this type behave**:

- Which callback handles messages
- What cursor and icon to use
- What style the window has

### Why it is required

Windows separates:

- Window _types_ (classes)
- Window _instances_

You must register a class before creating any window using it.