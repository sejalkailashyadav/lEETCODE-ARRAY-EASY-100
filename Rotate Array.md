**Leetcode 189: Rotate Array** step-by-step with 3 different methods (easy to optimized), detailed dry run, and final C++ code.

---

## 🔍 Problem Summary (Level-0):

You're given:

* An array `nums`
* A number `k`

👉 Rotate the array to the **right** by `k` steps.
✅ Do it **in-place** if possible.

---

### 🧠 Example:

Input: `nums = [1,2,3,4,5,6,7]`, `k = 3`
Output: `[5,6,7,1,2,3,4]`

---

## ✅ Approach 1: Brute Force (Rotate 1 step, k times)

### 🔁 Logic:

* Repeat `k` times:

  * Move last element to front (one step rotation)

### ⏱ Time: `O(n * k)`

📦 Space: `O(1)`

🚫 Too slow for large arrays or big `k`

---

## ✅ Approach 2: Extra Array (Simple and Fast)

### 💡 Logic:

* Create a new array
* Place each number at `(i + k) % n` position
* Copy back to original array

### ⏱ Time: `O(n)`

📦 Space: `O(n)` ❌ not in-place

---

### 🔸 Code:

```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        vector<int> temp(n);

        for (int i = 0; i < n; i++) {
            temp[(i + k) % n] = nums[i];
        }

        nums = temp;
    }
};
```

---

## ⚡ Approach 3: Reverse Method (✅ Optimized & In-Place)

### 💡 Idea:

To rotate right by `k`, do 3 reversals:

1. Reverse the **whole array**
2. Reverse the **first k elements**
3. Reverse the **remaining n - k elements**

---

### 🧠 Dry Run: `nums = [1,2,3,4,5,6,7]`, `k = 3`

* Step 1: reverse whole → `[7,6,5,4,3,2,1]`
* Step 2: reverse first 3 → `[5,6,7,4,3,2,1]`
* Step 3: reverse rest → `[5,6,7,1,2,3,4]` ✅

---

### 🔸 C++ Code:

```cpp
class Solution {
public:
    void reverse(vector<int>& nums, int start, int end) {
        while (start < end) {
            swap(nums[start], nums[end]);
            start++;
            end--;
        }
    }

    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n;  // In case k > n

        // Step 1: reverse full array
        reverse(nums, 0, n - 1);
        // Step 2: reverse first k elements
        reverse(nums, 0, k - 1);
        // Step 3: reverse remaining elements
        reverse(nums, k, n - 1);
    }
};
```

---

## ✅ Time & Space:

| Metric | Value           |
| ------ | --------------- |
| Time   | O(n)            |
| Space  | O(1) ✅ In-place |

---

## ✅ Summary of Approaches:

| Approach    | Time    | Space | Notes                        |
| ----------- | ------- | ----- | ---------------------------- |
| Brute Force | O(n\*k) | O(1)  | Slow for large input         |
| Extra Array | O(n)    | O(n)  | Fast but uses extra space    |
| **Reverse** | O(n)    | O(1)  | ✅ Best: In-place & efficient |

---
