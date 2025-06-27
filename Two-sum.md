[**LeetCode 1: Two Sum**](https://leetcode.com/problems/two-sum/) from the ground up. We’ll go step-by-step with:

✅ Easy approach (brute force)
✅ Optimized approach (using hash map)
✅ C++ code for both
✅ Visual iteration steps
✅ LeetCode-style final solution

---

## 🧠 Problem Statement:

> Given an array `nums` and an integer `target`, return **indices** of the two numbers such that they add up to `target`.

### Example:

```cpp
Input: nums = [2, 7, 11, 15], target = 9  
Output: [0, 1] // because nums[0] + nums[1] = 2 + 7 = 9
```

---

## 🔹 Step 1: Easy Brute Force Approach (Try All Pairs)

### ✅ Idea:

* Check all pairs `i`, `j` where `i < j`
* If `nums[i] + nums[j] == target`, return `[i, j]`

### 🧾 C++ Code:

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        for (int i = 0; i < nums.size(); i++) {
            for (int j = i + 1; j < nums.size(); j++) {
                if (nums[i] + nums[j] == target)
                    return {i, j};
            }
        }
        return {};
    }
};
```

---

## 📊 Visual Iteration Table

Let’s take: `nums = [2, 7, 11, 15], target = 9`

| i                                      | j | nums\[i] | nums\[j] | Sum = nums\[i] + nums\[j] | Matches target?       |
| -------------------------------------- | - | -------- | -------- | ------------------------- | --------------------- |
| 0                                      | 1 | 2        | 7        | 2 + 7 = 9                 | ✅ YES → return \[0,1] |
| (loop stops here since match is found) |   |          |          |                           |                       |

⛔ Time: O(n²)
✅ Space: O(1)

---

## 🔹 Step 2: Optimized Approach (Using Hash Map)

### ✅ Idea:

* Loop once
* For each element, calculate the **complement** (target - current value)
* If complement is already in map → solution found

### 🔁 Example Walkthrough (nums = \[2, 7, 11, 15], target = 9)

| i | nums\[i] | target - nums\[i] | Map Contents | Found Match?           |
| - | -------- | ----------------- | ------------ | ---------------------- |
| 0 | 2        | 7                 | {}           | ❌ No                   |
| 1 | 7        | 2                 | {2: 0}       | ✅ Yes → return \[0, 1] |

---

### 🧾 C++ Code (Optimized):

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> seen;
        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];
            if (seen.count(complement))
                return {seen[complement], i};
            seen[nums[i]] = i;
        }
        return {};
    }
};
```

⏱ Time: O(n)
📦 Space: O(n)

---

## ✅ LeetCode Solution (Same as Optimized)

This is the **standard accepted solution on LeetCode**, uses `unordered_map` as above.

You can submit the **optimized version** directly:
🔗 [Go to problem on LeetCode](https://leetcode.com/problems/two-sum/)

---

## 🏁 Summary:

| Approach        | Time  | Space | Suitable For |
| --------------- | ----- | ----- | ------------ |
| Brute Force     | O(n²) | O(1)  | Easy Start   |
| Hash Map (Best) | O(n)  | O(n)  | Interviews   |

---
