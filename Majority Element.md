## 🔍 Problem Summary (Level-0):

You are given an array `nums`, and you must **find the number that appears more than n/2 times**.

✅ You can assume this number **always exists**.

---

## 🧠 Examples:

### Example 1:

Input: `[3,2,3]`
n = 3 → n/2 = 1.5 → Majority appears > 1.5 times
Output: `3`

### Example 2:

Input: `[2,2,1,1,1,2,2]`
n = 7 → n/2 = 3.5 → Majority appears > 3.5 times
Output: `2`

---

## ✅ Approach 1: Hash Map (Simple)

### 💡 Logic:

* Count how many times each number appears
* Return the number whose count > n/2

### ⏱ Time: O(n)

📦 Space: O(n)

---

### 🔸 Code:

```cpp
#include <unordered_map>
using namespace std;

class Solution {
public:
    int majorityElement(vector<int>& nums) {
        unordered_map<int, int> count;
        int n = nums.size();

        for (int num : nums) {
            count[num]++;
            if (count[num] > n / 2)
                return num;
        }
        return -1; // should never happen as per problem
    }
};
```

---

## ⚡ Approach 2: Boyer-Moore Voting Algorithm (Optimized)

### 💡 Key Idea:

* Keep a **count** and a **candidate**
* If count is 0 → pick new candidate
* If current number == candidate → increase count
* Else → decrease count

This works **only because a majority element is guaranteed**.

---

### 🧠 Dry Run:

Input: `[2,2,1,1,1,2,2]`

| Step | Num | Candidate | Count |
| ---- | --- | --------- | ----- |
| 1    | 2   | 2         | 1     |
| 2    | 2   | 2         | 2     |
| 3    | 1   | 2         | 1     |
| 4    | 1   | 2         | 0     |
| 5    | 1   | 1         | 1     |
| 6    | 2   | 1         | 0     |
| 7    | 2   | 2         | 1     |

✅ Majority is 2

---

### ✅ Time: O(n)

📦 Space: O(1) ✅

---

### 🔸 Code (Boyer-Moore):

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int count = 0;
        int candidate = 0;

        for (int num : nums) {
            if (count == 0)
                candidate = num;
            count += (num == candidate) ? 1 : -1;
        }

        return candidate;
    }
};
```

---

## ✅ Summary:

| Method          | Time | Space    | Notes                     |
| --------------- | ---- | -------- | ------------------------- |
| Hash Map        | O(n) | O(n)     | Easy to understand        |
| **Boyer-Moore** | O(n) | **O(1)** | ✅ Best: efficient & clean |

---
