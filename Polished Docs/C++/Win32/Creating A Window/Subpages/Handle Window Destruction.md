---
# Step 11: Handle Window Destruction

This step is in the `WindowProcedure` function bound previously.

```cpp
case WM_DESTROY:
    PostQuitMessage(0);
    break;
```

### What it does

Signals the message loop to exit.

### Why it is required

This is how Windows cleanly terminates an application.

Without it:

- The app may never exit
- Resources may leak