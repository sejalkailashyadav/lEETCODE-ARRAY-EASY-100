Here’s the **complete Markdown (`.md`) solution file** for **LeetCode 1051. Height Checker** with:

* Problem Summary
* Step-by-step explanation
* Simple C++ solution
* Optimized explanation
* Test cases
---

### 📘 LeetCode 1051 - Height Checker

---
#### ✅ Problem Summary

You are given an array `heights` representing how students are currently standing.

To take a proper photo, they should be ordered in **non-decreasing** height order.
We need to **return the number of students** who are **not standing in the right position**.

---

### 🔸 Example

```text
Input:  heights = [1,1,4,2,1,3]
Output: 3

Explanation:
Original: [1,1,4,2,1,3]
Expected: [1,1,1,2,3,4]
Mismatch indices: 2, 4, 5 → Total = 3
```

---

### 🔰 Simple C++ Solution

```cpp
#include <vector>
#include <algorithm>
using namespace std;

int heightChecker(vector<int>& heights) {
    vector<int> expected = heights;     // Copy original
    sort(expected.begin(), expected.end());  // Sort to get expected positions
    
    int count = 0;
    for (int i = 0; i < heights.size(); ++i) {
        if (heights[i] != expected[i]) {
            count++;
        }
    }
    return count;
}
```

---

### 🧠 Key Idea (Step-by-Step)

1. **Copy** the original heights to a new array.
2. **Sort** the new array to get the expected order.
3. **Compare** each original height with the expected one.
4. **Count** mismatches.

---

### 🧪 Test Cases

| Input          | Output |
| -------------- | ------ |
| \[1,1,4,2,1,3] | 3      |
| \[5,1,2,3,4]   | 5      |
| \[1,2,3,4,5]   | 0      |
| \[3,2,1]       | 2      |
| \[1,2,2,1,1]   | 2      |

---

### ⚙️ Time & Space Complexity

| Aspect | Complexity |
| ------ | ---------- |
| Time   | O(n log n) |
| Space  | O(n)       |

* Sorting the array takes `O(n log n)`
* We use extra space for the `expected` array copy

---

### ✅ Final Notes

* This is a basic **sorting and comparison** problem.
* Real-world analogy: students standing incorrectly in a line for a photo shoot.
* Works well for values up to `heights.length <= 100`.

---
