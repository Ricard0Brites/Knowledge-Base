---
# std::unique_ptr

## Purpose

Exclusive ownership of heap memory.

---

## Key Properties

- Single owner
    
- Non-copyable
    
- Movable
    
- Zero overhead
    

---

## Lifetime

- Resource acquired on construction
    
- Automatically deleted on destruction
    

---

## Usage

```cpp
std::unique_ptr<Foo> p = std::make_unique<Foo>();
```

---

## When to Use

- Default choice for ownership
    
- Clear lifetime boundaries
    
- No sharing required
    

---

## Notes

- Replaces raw `new` / `delete`
    
- Prefer `make_unique`
