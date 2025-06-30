### ✅ Problem:

You are given an array `nums` containing `n` distinct numbers from the range `[0, n]`. One number is missing. You need to find it.

---

### 🧠 Intuition:

There are `n + 1` numbers from `0` to `n`, but the array has only `n` numbers. So, **1 number is missing**.

If we know the sum of all numbers from `0` to `n`, and subtract the sum of elements in `nums`, we get the missing number.

---

### 📘 Key Formula:

Sum of first `n` natural numbers is:

```
totalSum = n * (n + 1) / 2
```

Then:

```
missing = totalSum - actualSum
```

---

### 🔍 Step-by-step Example:

#### Input:

```cpp
nums = [3, 0, 1]
```

* n = 3 (because array has 3 numbers)
* Full range = \[0, 1, 2, 3]

1. totalSum = 3 × (3 + 1) / 2 = 6
2. actualSum = 3 + 0 + 1 = 4
3. missing = 6 - 4 = 2 ✅

---

### ✅ C++ Code:

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        int totalSum = n * (n + 1) / 2;
        
        int actualSum = 0;
        for (int num : nums)
            actualSum += num;
        
        return totalSum - actualSum;
    }
};
```

---

### 💡 Try Inputs:

```cpp
nums = {3, 0, 1};         // ➜ Output: 2
nums = {0, 1};            // ➜ Output: 2
nums = {9,6,4,2,3,5,7,0,1}; // ➜ Output: 8
```

---
