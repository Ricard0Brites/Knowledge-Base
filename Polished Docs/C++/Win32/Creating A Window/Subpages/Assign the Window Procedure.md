---
# Step 4: Assign the Window Procedure

```cpp
wc.lpfnWndProc = WindowProcedure;
```

### What it does

Tells Windows:

> "Use this function to send messages to windows of this class"

### Why it is required

Without a window procedure:

- Your window cannot process events
- The OS cannot safely interact with your application