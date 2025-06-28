### 🔍 Problem Statement (Level-0):

You are given an array `nums`.
You need to check:
👉 **Is there any number that appears **more than once**?**

✅ Return `true` if yes
❌ Return `false` if all numbers are different.

---

### 🧠 Example:

**Input:** `[1, 2, 3, 1]`
`1` is repeating → ✅ Return `true`

**Input:** `[1, 2, 3, 4]`
All numbers are unique → ❌ Return `false`

---

## 🔨 1. Brute Force Approach

### 💡 Logic:

Compare each element with every other element using 2 loops.

### ⏱️ Time Complexity:

`O(n^2)` → Very slow for large inputs

---

### 🧾 Code (Brute Force C++):

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool containsDuplicate(vector<int>& nums) {
    int n = nums.size();
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (nums[i] == nums[j])
                return true;
        }
    }
    return false;
}

int main() {
    vector<int> nums = {1, 2, 3, 1};
    cout << (containsDuplicate(nums) ? "true" : "false") << endl;
}
```

---

## ⚡ 2. Optimized Approach using Hash Set

### 💡 Logic:

* Use a `set` to track numbers we've seen.
* If a number appears again → it's a duplicate!

### 🔧 Why this works?

* `set` keeps only **unique** values.
* Checking if a value exists in a set is **O(1)** on average.

### ⏱️ Time Complexity:

`O(n)` — Fast and efficient

### 🧠 Space Complexity:

`O(n)` — To store seen values

---

### ✅ Optimized Code (C++ using `unordered_set`):

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
using namespace std;

bool containsDuplicate(vector<int>& nums) {
    unordered_set<int> seen;
    for (int num : nums) {
        if (seen.count(num)) {
            return true;
        }
        seen.insert(num);
    }
    return false;
}

int main() {
    vector<int> nums = {1, 2, 3, 1};
    cout << (containsDuplicate(nums) ? "true" : "false") << endl;
}
```

---

### 📊 Dry Run Example (Optimized):

**Input:** `[1, 2, 3, 1]`
`seen = {}`

| i | num | seen      | Duplicate? |
| - | --- | --------- | ---------- |
| 0 | 1   | `{}`      | No         |
| 1 | 2   | `{1}`     | No         |
| 2 | 3   | `{1,2}`   | No         |
| 3 | 1   | `{1,2,3}` | ✅ Yes      |

Return `true`

---

## ✅ Final LeetCode-Style C++ Solution:

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_set<int> seen;
        for (int num : nums) {
            if (seen.count(num))
                return true;
            seen.insert(num);
        }
        return false;
    }
};
```

---

### 👍 Summary:

| Approach    | Time  | Space | Code Simplicity | Use For             |
| ----------- | ----- | ----- | --------------- | ------------------- |
| Brute Force | O(n²) | O(1)  | Beginner level  | Very small arrays   |
| Hash Set    | O(n)  | O(n)  | Easy and Fast   | Best for most cases |

---
