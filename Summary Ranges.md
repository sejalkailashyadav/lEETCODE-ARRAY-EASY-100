### ✅ Problem Summary (Simple Words):

You are given a **sorted array** of **unique integers**.

👉 Your task is to:

* Group all **continuous numbers** into ranges.
* Format:

  * `"a->b"` if numbers go from a to b (e.g., \[2,3,4] → "2->4")
  * `"a"` if only one number is there (e.g., \[7] → "7")

---

### 🔍 Example:

#### Input:

```cpp
nums = [0,1,2,4,5,7]
```

#### Output:

```
["0->2", "4->5", "7"]
```

---

### 🔧 Step-by-Step Explanation:

We loop through the array and:

1. Keep track of **start** of current range.
2. Move forward until the next number is **not consecutive**.
3. Add the range `"start->end"` or just `"start"` to the result.
4. Repeat.

---

### 🧠 Visual Iteration (for \[0,1,2,4,5,7]):

| Start | i | nums\[i] | Action                        |
| ----- | - | -------- | ----------------------------- |
| 0     | 0 | 0        | Start of new range            |
| 0     | 1 | 1        | Still consecutive             |
| 0     | 2 | 2        | Still consecutive             |
| 0     | 3 | 4        | Not consecutive ➝ save "0->2" |
| 4     | 3 | 4        | New start                     |
| 4     | 4 | 5        | Still consecutive             |
| 4     | 5 | 7        | Not consecutive ➝ save "4->5" |
| 7     | 5 | 7        | New start                     |
|       |   |          | End ➝ save "7"                |

---

## 👨‍💻 C++ Code (LeetCode Submission):

```cpp
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> result;
        int n = nums.size();
        if (n == 0) return result;

        int start = nums[0];

        for (int i = 1; i <= n; i++) {
            // check if it's the end of a range
            if (i == n || nums[i] != nums[i - 1] + 1) {
                if (start == nums[i - 1]) {
                    result.push_back(to_string(start));
                } else {
                    result.push_back(to_string(start) + "->" + to_string(nums[i - 1]));
                }

                // Start new range if not at end
                if (i < n) start = nums[i];
            }
        }

        return result;
    }
};
```

---

### 🧪 Sample Test Run:

#### Input:

```cpp
nums = [0, 2, 3, 4, 6, 8, 9]
```

#### Output:

```
["0", "2->4", "6", "8->9"]
```

---

### 🧠 Time and Space Complexity:

* **Time:** O(n) → we go through the list once
* **Space:** O(1) extra (excluding output vector)

---
