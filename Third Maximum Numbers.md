## 🔍 Problem Summary:

You're given an array of integers.
👉 Find the **third distinct maximum number**.

* If it **does not exist**, return the **maximum number**.

---

### 🧠 Examples:

#### Example 1:

Input: `nums = [3, 2, 1]`
Output: `1`
✔ Third max is 1

#### Example 2:

Input: `nums = [1, 2]`
Output: `2`
✔ No third max, so return max (2)

#### Example 3:

Input: `nums = [2, 2, 3, 1]`
Output: `1`
✔ Distinct: \[3, 2, 1] → third is 1

---

## ✅ Plan:

We need the **top 3 distinct** numbers.

### Step-by-step logic:

* Use 3 variables: `first`, `second`, `third`
* Traverse array and update:

  * `first` if current > first
  * `second` if current between first and second
  * `third` if current between second and third
* **Skip duplicates**
* At the end, return `third` if it exists, else return `first`

---

## ✅ C++ Code:

```cpp
#include <vector>
#include <limits>
using namespace std;

class Solution {
public:
    int thirdMax(vector<int>& nums) {
        long first = LONG_MIN, second = LONG_MIN, third = LONG_MIN;

        for (int num : nums) {
            if (num == first || num == second || num == third)
                continue;

            if (num > first) {
                third = second;
                second = first;
                first = num;
            }
            else if (num > second) {
                third = second;
                second = num;
            }
            else if (num > third) {
                third = num;
            }
        }

        return third == LONG_MIN ? first : third;
    }
};
```

---

### ✅ Dry Run:

Input: `[2, 2, 3, 1]`
Distinct values: `[3, 2, 1]`

* First = 3
* Second = 2
* Third = 1
  ✅ Return: `1`

---

## ✅ Time and Space:

| Metric | Value                        |
| ------ | ---------------------------- |
| Time   | O(n)                         |
| Space  | O(1)  ✅ constant extra space |

---
