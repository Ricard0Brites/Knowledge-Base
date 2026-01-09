---
# RAII - Resource Acquisition Is Initialization

## Definition

Resource lifetime == object lifetime.

---

## What It Manages

- Memory
    
- Files
    
- Locks
    
- Sockets
    
- GPU/OS handles
    

---

## How It Works

- Acquire resource in constructor
    
- Release resource in destructor
    
- Scope controls lifetime
    

```cpp
struct File {
  FILE* f;
  File(const char* p) : f(fopen(p, "r")) {}
  ~File() { if (f) fclose(f); }
};
```

---

## Benefits

- No leaks
    
- Exception-safe
    
- Deterministic cleanup
    
- No manual `delete` / `free`
    

---

## Standard RAII Types

|Type|Resource| Links |
|---|---|---|
|`std::unique_ptr`|Heap memory|[[unique_ptr]]|
|`std::shared_ptr`|Shared ownership|[[shared_ptr]]|
|`std::vector`|Dynamic arrays|[[std Vector]] |
|`std::lock_guard`|Mutex|[[lock_guard]]|

---

## Rule of Thumb

> If you call `delete` or `free`, you probably skipped RAII.
