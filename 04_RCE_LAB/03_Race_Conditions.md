# Race Conditions (TOCTOU)
**Metaphor: The Ticket Booth & Time Gap**

---

## Concept

**TOCTOU** = Time-Of-Check to Time-Of-Use.

Imagine a ticket booth.
1. **Check:** The seller asks "Is the seat free?" -> System says "Yes".
2. **Gap:** The seller turns to take your money. (1 second delay).
3. **Use:** You pay.

**The Hack:** In that 1-second gap, another process (The Architect) buys the ticket.
When the seller turns back, the reality has changed, but their logic hasn't.

---

## C++ Example

```cpp
#include <iostream>
#include <fstream>
#include <unistd.h>

void process_file(const char* filename) {
    // 1. CHECK (Security Check)
    if (access(filename, W_OK) == 0) {
        
        // --- THE GAP (Reality Lag) ---
        // Attacker swaps the file here!
        sleep(1); 
        
        // 2. USE (Action)
        std::ofstream ofs(filename);
        ofs << "HACKED"; 
    }
}
```
Result
The system checks a harmless file, but writes to a critical file (like /etc/passwd) because the pointer changed during the pause.

Business Analogy
The Gap = Time between "Budget Approval" and "Contract Signing".

The Hack = Inserting a new clause or vendor exactly when the guard is down.

Defense = Atomic Transactions (Check and Use must happen instantly).
