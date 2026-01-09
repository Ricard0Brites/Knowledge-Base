---
# std::vector

## Purpose

RAII-managed dynamic array.

---

## Key Properties

- Contiguous storage
    
- Automatic resizing
    
- Owns its memory
    

---

## Lifetime

- Memory allocated on growth
    
- Automatically freed on destruction
    

---

## Usage

```cpp
std::vector<int> v{1, 2, 3};
```

---

## When to Use

- Dynamic arrays
    
- Cache-friendly iteration
    
- Default container choice
    

---

## Notes

- No manual `new[]` / `delete[]`
    
- Bounds-checked access via `at()`
