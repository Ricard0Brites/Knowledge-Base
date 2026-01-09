---
# Step 2: Define a Window Procedure

```cpp
LRESULT CALLBACK WindowProcedure(HWND hWnd, UINT msg, WPARAM wParam, LPARAM lParam);
```

### What it does

Acts as the **callback function** Windows uses to communicate with your application.

All events go through this function:

- Closing the window
- Resizing
- Keyboard and mouse input

### Why it is required

Windows is event-driven. Your program must provide a function that receives and responds to OS messages.

Without this, Windows has no way to notify your application of events.