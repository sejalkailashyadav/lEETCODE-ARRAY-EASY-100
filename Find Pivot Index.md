### ✅ Goal:

Find an index `i` where the sum of all elements to the **left** of `i` is equal to the sum of all elements to the **right** of `i`.

---

### 🧠 Intuition:

Instead of calculating left and right sums for every index (which takes time), we can use the **total sum** of the array.

### 📘 Key Formula:

At any index `i`, if

```
leftSum == totalSum - leftSum - nums[i]
```

then `i` is the pivot index.

This works because:

* `leftSum` is the sum before index `i`
* `totalSum - leftSum - nums[i]` is the sum after index `i`

---

### 🔍 Step-by-step Example:

#### Input:

```cpp
nums = [1, 7, 3, 6, 5, 6]
```

#### Step 1: Find total sum:

```
totalSum = 1+7+3+6+5+6 = 28
```

#### Step 2: Loop through array and maintain `leftSum`:

| i | nums\[i] | leftSum | rightSum (computed) | Is Pivot? |
| - | -------- | ------- | ------------------- | --------- |
| 0 | 1        | 0       | 28 - 0 - 1 = 27     | No        |
| 1 | 7        | 1       | 28 - 1 - 7 = 20     | No        |
| 2 | 3        | 8       | 28 - 8 - 3 = 17     | No        |
| 3 | 6        | 11      | 28 - 11 - 6 = 11    | ✅ Yes     |

Return `3`

---

### ✅ Final C++ Code:

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int totalSum = 0;
        for (int num : nums)
            totalSum += num;

        int leftSum = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (leftSum == totalSum - leftSum - nums[i])
                return i;
            leftSum += nums[i];
        }

        return -1;
    }
};
```

---

### 🧪 Try Inputs:

```cpp
nums = {1, 7, 3, 6, 5, 6}; // ➜ Output: 3
nums = {1, 2, 3};          // ➜ Output: -1
nums = {2, 1, -1};         // ➜ Output: 0
```

---
