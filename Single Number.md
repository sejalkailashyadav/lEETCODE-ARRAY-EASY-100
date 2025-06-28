## 🔍 Problem Statement (Level-0):

You are given a list of numbers where:

* Every number appears **exactly twice**
* Except **one number**, which appears **only once**

👉 Your job: **Find that single number**

### 🧠 Example:

Input: `[2, 2, 1]`
Output: `1`

Input: `[4, 1, 2, 1, 2]`
Output: `4`

---

## 🛠️ Step-by-Step Approaches

---

### ✅ 1. **Brute Force (Using Map)**

#### 💡 Logic:

* Count how many times each number appears using a map.
* Return the number which appears only once.

#### ⏱️ Time: `O(n)`

📦 Space: `O(n)` → Not allowed by constraint (says **constant extra space only**)

```cpp
#include <unordered_map>
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        unordered_map<int, int> freq;
        for (int num : nums) {
            freq[num]++;
        }
        for (auto pair : freq) {
            if (pair.second == 1)
                return pair.first;
        }
        return -1; // shouldn't reach here
    }
};
```

---

### ✅ 2. **Optimal Solution (Using Bit Manipulation - XOR)**

#### 💡 Core Idea:

Use **XOR** property:

```
a ^ a = 0  
a ^ 0 = a
```

So if we XOR all elements:

* Pairs cancel out
* Only the single number remains

#### ✅ Example:

```
Input: [4,1,2,1,2]
XOR:   4 ^ 1 ^ 2 ^ 1 ^ 2
=>     (1 ^ 1) = 0
=>     (2 ^ 2) = 0
=>     0 ^ 0 ^ 4 = 4
```

#### ⏱️ Time: `O(n)`

📦 Space: `O(1)` ✅

---

### 🚀 Final Optimized Code (LeetCode Accepted):

```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int result = 0;
        for (int num : nums) {
            result ^= num;
        }
        return result;
    }
};
```

---

### 📊 Dry Run of XOR Method:

Input: `[2, 2, 1]`

| Step | XOR Operation | Result |
| ---- | ------------- | ------ |
| 1    | 0 ^ 2         | 2      |
| 2    | 2 ^ 2         | 0      |
| 3    | 0 ^ 1         | 1      |

✅ Output: `1`

---

### ✅ Summary:

| Method    | Time     | Space    | Notes                        |
| --------- | -------- | -------- | ---------------------------- |
| HashMap   | O(n)     | O(n)     | Easy but uses extra memory   |
| XOR Trick | **O(n)** | **O(1)** | ✅ Best — no extra space used |

---
