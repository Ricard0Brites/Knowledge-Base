---
# Increment/Decrement Notes
- `++x` increments before evaluation
- `x++` increments after evaluation
- Works on integers, pointers, and iterators

```cpp
int arr[3] = {1,2,3};
int* p = arr;
p++;   // moves pointer to arr[1]
```