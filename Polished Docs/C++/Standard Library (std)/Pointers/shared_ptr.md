---
# std::shared_ptr

## Purpose

Shared ownership of heap memory.

---

## Key Properties

- Reference-counted
    
- Copyable
    
- Thread-safe control block
    

---

## Lifetime

- Resource destroyed when last owner releases
    

---

## Usage

```cpp
auto p = std::make_shared<Foo>();
```

---

## When to Use

- Multiple owners required
    
- Ownership not hierarchical
    

---

## Notes

- Higher overhead than `unique_ptr`
    
- Avoid cycles (use `std::weak_ptr`)
