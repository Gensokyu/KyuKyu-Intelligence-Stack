# Heap Use-After-Free (UAF)
**Metaphor: Dangling Keys & Amazon Warehouse**

---

## Concept

The heap is an Amazon warehouse.
You request space, store goods, then release it.

A Use-After-Free occurs when:
- The storage is returned to the warehouse
- But you keep the key
- And try to access the space later

The space may now belong to someone else.

---

## C++ Example

```cpp
#include <iostream>

int* getData() {
    int* box = new int(42);
    delete box;
    return box; // dangling key
}

int main() {
    int* data = getData();
    std::cout << *data << std::endl; // undefined behavior
}
```
## Result
The program may:
* Print garbage
* Crash
* Appear to work (most dangerous)

## Business Analogy
* **Warehouse slot** = process / report
* **Key** = habit / assumption
* **New tenant** = changed reality

**You are making decisions using:**
1. Old reports
2. Former employee logic
3. Market conditions that no longer exist
