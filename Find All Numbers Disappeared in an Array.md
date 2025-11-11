###  Problem:

You are given an array `nums` of size `n`. Each number is in the range `[1, n]`, but some numbers are **missing**, and some may **appear twice**. Return all numbers in the range `[1, n]` that **do not appear in `nums`**.

---

### 🧠 Intuition:

We want to find which numbers from `1` to `n` are **missing** from the array.

We are also told:

* Do this in **O(n)** time
* Do **not** use extra space (except for the result list)

So, we’ll use a **clever trick**: marking numbers in the array itself.

---

### 🎯 Key Idea (Index Marking Trick):

We will mark visited numbers by **making elements at certain indexes negative**.

#### Steps:

1. For every number `num` in the array:

   * Mark index `abs(num) - 1` as negative to show "we’ve seen that number".

2. After that, any index `i` that still has a **positive** number means:

   * Number `i + 1` was **never seen**, so it’s missing.

---

### 🔍 Step-by-step Example:

```cpp
Input: nums = [4,3,2,7,8,2,3,1]
```

**Initial indexes:**

```
[4, 3, 2, 7, 8, 2, 3, 1]
```

**Marking steps:**

* mark index 3 → \[-4, 3, 2, 7, 8, 2, 3, 1]
* mark index 2 → \[-4, 3, -2, 7, 8, 2, 3, 1]
* mark index 1 → \[-4, -3, -2, 7, 8, 2, 3, 1]
* mark index 6 → \[-4, -3, -2, -7, 8, 2, 3, 1]
* mark index 7 → \[-4, -3, -2, -7, 8, 2, 3, -1]
* mark index 1 again → already negative
* mark index 2 again → already negative
* mark index 0 → \[-4, -3, -2, -7, 8, 2, 3, -1]

**Final array:** `[-4, -3, -2, -7, 8, 2, 3, -1]`

Indexes 4 and 5 are still positive → missing numbers are `5` and `6`

---

### ✅ C++ Code:

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        for (int i = 0; i < nums.size(); i++) {
            int index = abs(nums[i]) - 1;
            if (nums[index] > 0)
                nums[index] = -nums[index]; // Mark as visited
        }

        vector<int> result;
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] > 0)  // Not visited
                result.push_back(i + 1);
        }

        return result;
    }
};
```

---

### 🧪 Test Inputs:

```cpp
nums = {4,3,2,7,8,2,3,1}; // ➜ Output: [5,6]
nums = {1,1};             // ➜ Output: [2]
```

---
