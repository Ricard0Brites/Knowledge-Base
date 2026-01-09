---
# std::lock_guard

## Purpose

Scoped mutex locking.

---

## Key Properties

- Non-copyable
    
- Locks on construction
    
- Unlocks on destruction
    

---

## Lifetime

- Mutex held for scope duration
    

---

## Usage

```cpp
std::lock_guard<std::mutex> lock(m);
```

---

## When to Use

- Simple critical sections
    
- Exception-safe locking
    

---

## Notes

- Zero runtime overhead
    
- Prefer over manual `lock()` / `unlock()`
