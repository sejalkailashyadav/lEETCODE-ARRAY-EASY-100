**Leetcode 283: Move Zeroes** in a **level-0 beginner-friendly** way with step-by-step logic, dry run, and optimized C++ code.

---

## 🔍 Problem Summary:

You're given an array like:

```cpp
nums = [0, 1, 0, 3, 12]
```

👉 Move all **zeroes** to the **end**
✅ Keep the **order** of non-zero elements
✅ Do this **in-place** (no extra array)

---

## 🧠 Example:

**Input:** `[0, 1, 0, 3, 12]`
**Output:** `[1, 3, 12, 0, 0]`

We moved all non-zero elements to the front and put all zeros at the end.

---

## ✅ Step-by-Step Logic (Two Pointers):

1. Use a pointer `lastNonZeroIndex = 0`
2. Loop through the array:

   * If current number is **not 0**, put it at `nums[lastNonZeroIndex]` and increment `lastNonZeroIndex`
3. After loop, fill the rest with zeros

---

## 🔁 Dry Run:

**Input:** `[0, 1, 0, 3, 12]`

| i | nums\[i] | Action                          | Result         |
| - | -------- | ------------------------------- | -------------- |
| 0 | 0        | skip                            | \[0,1,0,3,12]  |
| 1 | 1        | move to index 0, ++lastZero = 1 | \[1,1,0,3,12]  |
| 2 | 0        | skip                            | \[1,1,0,3,12]  |
| 3 | 3        | move to index 1, ++lastZero = 2 | \[1,3,0,3,12]  |
| 4 | 12       | move to index 2, ++lastZero = 3 | \[1,3,12,3,12] |

**Final step:** Fill zeros from index 3 to end
👉 Output: `[1,3,12,0,0]`

---

## ✅ Final C++ Code:

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int lastNonZeroIndex = 0;

        // Step 1: Move all non-zero elements forward
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] != 0) {
                nums[lastNonZeroIndex] = nums[i];
                lastNonZeroIndex++;
            }
        }

        // Step 2: Fill the rest with 0s
        for (int i = lastNonZeroIndex; i < nums.size(); i++) {
            nums[i] = 0;
        }
    }
};
```

---

## ⏱ Time & Space:

| Metric | Value            |
| ------ | ---------------- |
| Time   | O(n)             |
| Space  | O(1)  ✅ In-place |

---

## ✅ Summary:

| Step          | Action                       |
| ------------- | ---------------------------- |
| Non-zero pass | Push all non-zero forward    |
| Fill zeros    | Remaining positions set to 0 |
| In-place      | No new array used            |

---
