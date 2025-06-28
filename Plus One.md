## 🔍 Problem Summary (Simple Explanation):

You're given a number as an array of digits, like this:

```cpp
digits = [1, 2, 3] // means number 123
```

Your task is:
👉 **Add 1 to this number**, and return the result as a digit array.

---

## 🧠 Examples:

| Input         | Output        | Why             |
| ------------- | ------------- | --------------- |
| \[1, 2, 3]    | \[1, 2, 4]    | 123 + 1 = 124   |
| \[4, 3, 2, 1] | \[4, 3, 2, 2] | 4321 + 1 = 4322 |
| \[9]          | \[1, 0]       | 9 + 1 = 10      |
| \[9, 9]       | \[1, 0, 0]    | 99 + 1 = 100    |

---

## ✅ Step-by-Step Logic:

1. **Start from the last digit**
2. If it’s less than 9:

   * Just add 1 and return
3. If it’s 9:

   * Set it to 0 (carry 1)
4. If all digits are 9 (like \[9, 9]):

   * Make space for one more digit at the beginning (insert 1)

---

## 🔁 Dry Run: Input = \[9, 9]

| Index | Digit | Action       | New Value  | Carry |
| ----- | ----- | ------------ | ---------- | ----- |
| 1     | 9     | 9+1 = 10 → 0 | 0          | 1     |
| 0     | 9     | 9+1 = 10 → 0 | 0          | 1     |
|       | done  | insert 1     | \[1, 0, 0] | -     |

---

## ✅ Final C++ Code (Clean & Accepted):

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int n = digits.size();

        // Start from the end and go backwards
        for (int i = n - 1; i >= 0; i--) {
            if (digits[i] < 9) {
                digits[i]++;      // just add 1
                return digits;
            }
            digits[i] = 0;        // carry over
        }

        // If we're here, all digits were 9 → [9,9] → [1,0,0]
        digits.insert(digits.begin(), 1);
        return digits;
    }
};
```

---

## ⏱ Time and Space:

| Complexity | Value                               |
| ---------- | ----------------------------------- |
| Time       | O(n)                                |
| Space      | O(1) extra (excluding result array) |

---
