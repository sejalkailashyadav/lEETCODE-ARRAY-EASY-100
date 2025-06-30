Let’s solve **LeetCode 645: Set Mismatch** in a beginner-friendly, step-by-step way.

---

### ✅ Problem:

You are given an array `nums` that should contain all numbers from `1` to `n`, but:

* One number is **duplicated**
* One number is **missing**

Your task is to return a vector of two values:

```
[duplicated_number, missing_number]
```

---

### 🧠 Intuition:

This is similar to the previous problem (like 448), but now:

* One number appears **twice**
* One number is **missing**

We can use the same trick: **marking indexes** by negating values.

---

### 🎯 Marking Logic (Index-based approach):

1. Loop through the array.
2. For each number, go to `abs(nums[i]) - 1` index.
3. If the number at that index is already negative → it’s **duplicated**
4. After marking, check all indexes:

   * If `nums[i]` is still positive → then `i + 1` is the **missing** number

---

### 🔍 Step-by-step Example:

#### Input:

```cpp
nums = [1, 2, 2, 4]
```

**Initial:**

* n = 4 → valid numbers = \[1, 2, 3, 4]

**Marking phase:**

* i = 0 → mark index 0 → nums\[0] becomes -1 → `[-1, 2, 2, 4]`
* i = 1 → mark index 1 → nums\[1] becomes -2 → `[-1, -2, 2, 4]`
* i = 2 → index 1 already negative → **duplicate = 2**
* i = 3 → mark index 3 → nums\[3] becomes -4 → `[-1, -2, 2, -4]`

**Now find missing:**

* Index 2 has positive value → **missing = 3**

✅ Final answer: `[2, 3]`

---

### ✅ C++ Code:

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Solution {
public:
    vector<int> findErrorNums(vector<int>& nums) {
        int dup = -1, missing = -1;

        // Step 1: Mark the indices
        for (int num : nums) {
            int index = abs(num) - 1;
            if (nums[index] < 0)
                dup = abs(num); // Found duplicate
            else
                nums[index] = -nums[index]; // Mark as visited
        }

        // Step 2: Find the missing number
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] > 0)
                missing = i + 1; // This index was never marked
        }

        return {dup, missing};
    }
};
```

---

### 🧪 Try Inputs:

```cpp
nums = {1, 2, 2, 4};   // ➜ Output: [2, 3]
nums = {1, 1};         // ➜ Output: [1, 2]
nums = {3, 2, 3, 4, 6, 5}; // ➜ Output: [3, 1]
```

---
