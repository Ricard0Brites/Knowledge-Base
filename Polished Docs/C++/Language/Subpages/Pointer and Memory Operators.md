---
# Pointer and Memory Operators
| Operator | Description |
|----------|-------------|
| `&`      | Address-of |
| `*`      | Dereference |
| `->`     | Access member via pointer |
| `.`      | Access member |
| `new`    | Allocate memory on heap and call constructor |
| `new[]`  | Allocate array on heap |
| `delete` | Deallocate memory allocated with `new` and call destructor |
| `delete[]` | Deallocate array allocated with `new[]` |
| `malloc` / `calloc` | C-style heap allocation (raw memory) |
| `free`   | C-style deallocation |

**Notes on heap vs stack:**

- **Stack allocation:** automatic objects, e.g. `Foo a;`  
  - Destroyed at scope exit  
  - No manual `delete` required  

- **Heap allocation:** dynamic objects, e.g. `auto p = new Foo();`  
  - Must be manually deleted (`delete p;`)  
  - Can store in `std::unique_ptr`/`std::shared_ptr` for RAII