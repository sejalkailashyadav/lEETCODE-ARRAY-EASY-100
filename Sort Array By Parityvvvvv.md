**Leetcode 905: Sort Array By Parity** in **very simple steps** with explanation and optimized C++ solution.

---

##  Problem:

You are given an array of integers `nums`.
You need to **move all even numbers to the front** and all **odd numbers to the back**.

Order **between even or odd doesn't matter**.

---

###  Example 1:

```
Input:  [3, 1, 2, 4]
Even:   [2, 4]
Odd:    [3, 1]
Output: [2, 4, 3, 1] ✅ or any valid version like [4,2,1,3]
```

### 🔹 Example 2:

```
Input:  [0]
Output: [0]
(0 is even, so valid)
```

---

## 🔸 Approach 1: Extra Space (Simple)

### ✅ Steps:

* Create a new array.
* First add all even numbers.
* Then add all odd numbers.

### ⏱️ Time: O(n)

### 📦 Space: O(n)

---

### ✅ C++ Code:

```cpp
class Solution {
public:
    vector<int> sortArrayByParity(vector<int>& nums) {
        vector<int> result;
        for (int num : nums) {
            if (num % 2 == 0) result.push_back(num); // Even
        }
        for (int num : nums) {
            if (num % 2 != 0) result.push_back(num); // Odd
        }
        return result;
    }
};
```

---

## 🔸 Approach 2: Two Pointer (In-Place & Optimized ✅)

### ✅ Steps:

* Use two pointers: `i = 0`, `j = nums.size() - 1`.
* Loop through array:

  * If `nums[i]` is even → keep it, move `i++`.
  * If `nums[i]` is odd → swap it with `nums[j--]`.

You may build a **new array** or modify **in-place**.

---

### ⏱️ Time: O(n)

### 📦 Space: O(1) (if done in-place)

---

### ✅ LeetCode C++ Optimized Version:

```cpp
class Solution {
public:
    vector<int> sortArrayByParity(vector<int>& nums) {
        int i = 0, j = nums.size() - 1;
        while (i < j) {
            if (nums[i] % 2 > nums[j] % 2) {
                swap(nums[i], nums[j]);
            }
            if (nums[i] % 2 == 0) i++;
            if (nums[j] % 2 == 1) j--;
        }
        return nums;
    }
};
```

---

## 🔹 Visual Walkthrough:

Input: `[3, 1, 2, 4]`
Initial: `i = 0 (3), j = 3 (4)`

* 3 is odd, 4 is even → swap → `[4, 1, 2, 3]`
* Now `i = 0`, 4 is even → i++
* i = 1 (1), j = 2 (2) → swap → `[4, 2, 1, 3]`
* Done ✅

---

### Final Output: Any even-odd mix like `[4,2,1,3]` is valid.

---
