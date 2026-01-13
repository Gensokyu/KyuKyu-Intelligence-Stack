# Side-Channel Attacks
**Metaphor: Feynman, Safe Cracking & Timing Analysis**

---

## Concept

A side-channel attack does not break the lock.
It listens.

Examples:
- Time taken to respond
- Power usage
- Sound
- Heat

Information leaks through behavior, not interfaces.

---

## C++ Timing Example

```cpp
#include <chrono>
#include <string>

bool checkPassword(const std::string& input) {
    const std::string secret = "kyukyu";
    for (size_t i = 0; i < secret.size(); i++) {
        if (input[i] != secret[i]) return false;
    }
    return true;
}
```
Issue:
Comparison exits early. Time reveals how many characters are correct.

Feynman Safe Metaphor
Feynman didn’t know combinations. He listened to clicks and delays. Humans do the same unconsciously.

Business Side-Channels
Signals that leak truth:
Delayed replies

Over-explaining

Defensive tone

Sudden politeness

Avoidance of specifics

"Words lie. Timing doesn’t."

KyuKyu Interpretation
Side-channel analysis is:

Observing stress instead of claims

Measuring hesitation instead of promises

Tracking response time instead of KPIs

Mitigation Principle: Align intent with execution speed. Remove unnecessary delays. Control leaks before it breaks.
