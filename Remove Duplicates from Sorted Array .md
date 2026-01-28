**LeetCode Problem 26: Remove Duplicates from Sorted Array** with:

*  Simple explanation
*  Table-based visual iteration
*  C++ code
  ✅ LeetCode-style return & in-place update

---

### 🧠 Basic Idea (Level-0 Explanation)

Since the array is **already sorted**, all **duplicate values will be next to each other**.

We just need to **move all unique values to the front**, and **skip the duplicates**.
We do this **in-place** (without using extra space).

---

### 🪜 Step-by-Step Logic

* Use **two pointers**:

  * `i` points to the **last unique value's position**.
  * `j` goes through each element in the array.

* If `nums[j] != nums[i]`, it means we found a new unique value.
  So we do `i++` and update `nums[i] = nums[j]`.

* At the end, the **first (i + 1)** elements are unique.

---

### 📊 Iteration Table (Example: `[0,0,1,1,1,2,2,3,3,4]`)

| j (current) | nums\[j] | i (last unique index) | Action                | Updated nums      |
| ----------- | -------- | --------------------- | --------------------- | ----------------- |
| 1           | 0        | 0                     | duplicate → skip      | `[0,0,...]`       |
| 2           | 1        | 0                     | new → i++, nums\[1]=1 | `[0,1,...]`       |
| 3           | 1        | 1                     | duplicate → skip      | `[0,1,...]`       |
| 4           | 1        | 1                     | duplicate → skip      | `[0,1,...]`       |
| 5           | 2        | 1                     | new → i++, nums\[2]=2 | `[0,1,2,...]`     |
| 6           | 2        | 2                     | duplicate → skip      | `[0,1,2,...]`     |
| 7           | 3        | 2                     | new → i++, nums\[3]=3 | `[0,1,2,3,...]`   |
| 8           | 3        | 3                     | duplicate → skip      | `[0,1,2,3,...]`   |
| 9           | 4        | 3                     | new → i++, nums\[4]=4 | `[0,1,2,3,4,...]` |

🔚 `i = 4` → Return `i + 1 = 5`
✅ Result: `nums = [0, 1, 2, 3, 4, _, _, _, _, _]`

---

### ✅ C++ Code (LeetCode Solution)

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) return 0;  // edge case

        int i = 0;  // pointer for unique values
        for (int j = 1; j < nums.size(); j++) {
            if (nums[j] != nums[i]) {
                i++;  // move to next unique slot
                nums[i] = nums[j];  // copy the unique value
            }
        }
        return i + 1;  // number of unique elements
    }
};
```

---

### 🚀 Time & Space Complexity

* **Time**: O(n) → each element is visited once
* **Space**: O(1) → in-place modification, no extra space used

---

### ✅ LeetCode Judge Works Like:

```cpp
int[] nums = {0,0,1,1,1,2,2,3,3,4};
int[] expectedNums = {0,1,2,3,4};

int k = removeDuplicates(nums);

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

---
