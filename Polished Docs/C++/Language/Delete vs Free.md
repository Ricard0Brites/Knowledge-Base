---
# Delete vs Free

## Core Rule

Allocation and deallocation **must match**.

|Allocate|Deallocate|Destructor|
|---|---|---|
|`new`|`delete`|Yes|
|`new[]`|`delete[]`|Yes (each)|
|`malloc` / `calloc` / `realloc`|`free`|No|

---

## `delete`

- C++ operator
    
- Type-aware
    
- Calls destructor
    
- Heap only (via `new`)
    

```cpp
Foo* f = new Foo();
delete f;
```

---

## `free`

- C function
    
- Raw memory
    
- No destructors
    
- Heap only (via `malloc`)
    

```cpp
Foo* f = (Foo*)malloc(sizeof(Foo));
free(f);
```

---

## Stack Clarification

- Stack memory is **automatic**
    
- Never use `delete` or `free`
    

```cpp
Foo f; // auto lifetime
```

---

## Invalid Usage

- `new` + `free` → undefined behavior
    
- `malloc` + `delete` → undefined behavior
