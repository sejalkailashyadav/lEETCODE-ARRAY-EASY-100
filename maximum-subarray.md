**[Leetcode 53: Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)** step-by-step from a **beginner (level-0)** view, with small dry runs, C++ code, and optimization.

---

## 🔍 Problem Summary:

Given an integer array `nums`,
👉 Find the **contiguous subarray (with at least one number)** which has the **largest sum**,
and return its sum.

---

### 🧠 Example 1:

**Input:** `nums = [-2,1,-3,4,-1,2,1,-5,4]`
**Output:** `6`
✅ Subarray: `[4,-1,2,1]` → sum = 6

---

## ✅ Step-by-Step Explanation:

We need to find a continuous block of numbers whose **sum is maximum**.

---

## ❌ Brute Force (Not Recommended)

Check every subarray and find the max sum.
⏱ Time: O(n²) or worse
📦 Space: O(1)

---

## ✅ Kadane’s Algorithm (Best and Easy)

### 💡 Key Idea:

As you move through the array, keep track of:

* `currentSum` → the best sum ending **at this point**
* `maxSum` → the best sum **seen so far**

If `currentSum` becomes negative, **start fresh** from the next number.

---

### 🧾 C++ Code:

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int currentSum = nums[0];
        int maxSum = nums[0];

        for (int i = 1; i < nums.size(); i++) {
            // If previous sum was bad, restart from current number
            currentSum = max(nums[i], currentSum + nums[i]);
            maxSum = max(maxSum, currentSum);
        }

        return maxSum;
    }
};
```

---

## 🔁 Dry Run:

Input: `[-2,1,-3,4,-1,2,1,-5,4]`

| i | num | currentSum        | maxSum |
| - | --- | ----------------- | ------ |
| 0 | -2  | -2                | -2     |
| 1 | 1   | max(1, -2+1) = 1  | 1      |
| 2 | -3  | max(-3, 1-3) = -2 | 1      |
| 3 | 4   | max(4, -2+4) = 4  | 4      |
| 4 | -1  | max(-1, 4-1) = 3  | 4      |
| 5 | 2   | max(2, 3+2) = 5   | 5      |
| 6 | 1   | max(1, 5+1) = 6   | 6 ✅    |
| 7 | -5  | max(-5, 6-5) = 1  | 6      |
| 8 | 4   | max(4, 1+4) = 5   | 6      |

✅ Final answer = `6`

---

## ✅ Time and Space:

| Metric | Value |
| ------ | ----- |
| Time   | O(n)  |
| Space  | O(1)  |

---

## 🔥 Summary:

* **Brute force** = slow
* ✅ **Kadane’s Algorithm** = efficient and simple
* Handles negatives and mixed values well

---
