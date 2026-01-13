# Stack Overflow
**Metaphor: Postboxes & Return Address Overwrite**

---

## Concept

The stack is a row of postboxes.
Each function call gets its own box.
At the end of the row sits the **return address** — where execution goes next.

A Stack Overflow happens when:
- You put too much mail into one box
- The overflow spills into the next box
- Eventually, you overwrite the return address

Control is lost.

---

## Business Analogy

- Postboxes = responsibilities
- Letters = data / tasks
- Return address = decision authority

When one role, report, or Excel file absorbs more responsibility than designed,
execution jumps to the wrong owner.

---

## C++ Example

```cpp
#include <cstring>
#include <iostream>

void vulnerable() {
    char mailbox[8];
    std::strcpy(mailbox, "THIS_IS_TOO_LONG");
}

int main() {
    vulnerable();
    std::cout << "Returned safely\n";
}
```
What happens:

mailbox expects 8 bytes
Input writes beyond its boundary
Stack memory is corrupted
In real systems, this can redirect execution.

KyuKyu Interpretation

Stack Overflow in organizations:
One person becomes a dependency sink
Informal responsibility overwrites formal structure
Decisions execute from the wrong address
