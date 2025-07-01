 **LeetCode 35: Search Insert Position** in a simple, step-by-step, beginner-friendly way using **C++** with an explanation and a LeetCode-submit-ready code.

---

### ✅ Problem Summary (Simple Words):

You’re given a **sorted array** (no duplicates) and a `target` number.

You need to:

* Return the **index** if the target is found.
* If not found, return the **index where it should be inserted** to keep the array sorted.

🧠 Must solve in **O(log n)** ➝ This means: **Binary Search**

---

### 🔍 Example:

#### Input:

```cpp
nums = [1, 3, 5, 6], target = 5
```

* 5 is found at index 2 ➝ ✅ Output: `2`

#### Input:

```cpp
nums = [1, 3, 5, 6], target = 2
```

* 2 is not found. It should be inserted at index 1 ➝ ✅ Output: `1`

---

### 🔧 Binary Search Approach (O(log n)):

1. Start with `low = 0`, `high = n - 1`.
2. Find `mid = (low + high) / 2`.
3. If `nums[mid] == target`, return `mid`.
4. If `nums[mid] < target`, search right half (`low = mid + 1`)
5. If `nums[mid] > target`, search left half (`high = mid - 1`)
6. If not found, `low` will be the **insert position**.

---

## 👨‍💻 C++ Code (LeetCode Submission):

```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int low = 0, high = nums.size() - 1;

        while (low <= high) {
            int mid = (low + high) / 2;

            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        // Not found, insert position is low
        return low;
    }
};
```

---

### 🔁 Visual (nums = \[1,3,5,6], target = 2):

| Step | low | mid | high | nums\[mid] | Action               |
| ---- | --- | --- | ---- | ---------- | -------------------- |
| 1    | 0   | 1   | 3    | 3          | target < mid → left  |
| 2    | 0   | 0   | 0    | 1          | target > mid → right |
| 3    | 1   | -   | 0    | -          | loop ends → return 1 |

---

### 🧠 Time & Space Complexity:

* **Time:** O(log n) → binary search
* **Space:** O(1)

---
