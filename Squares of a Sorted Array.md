**LeetCode 977: Squares of a Sorted Array** step-by-step in a **beginner-friendly** and **optimized** way using **C++**, with full explanation and **LeetCode-submit-ready code**.

---

### ✅ Problem Summary (Simple Words):

You are given a **sorted array** (could have negative and positive numbers).
You need to:

1. **Square each number**
2. Return a new array where all squares are **sorted in non-decreasing order**

---

### 🔍 Example:

#### Input:

```
nums = [-4, -1, 0, 3, 10]
```

#### Steps:

* Squared: \[16, 1, 0, 9, 100]
* Sorted: ✅ \[0, 1, 9, 16, 100]

---

### 🧠 Brute-force (Easy but Not Optimal):

1. Square all elements.
2. Sort the array.

```cpp
vector<int> sortedSquares(vector<int>& nums) {
    for (int &n : nums) {
        n = n * n;
    }
    sort(nums.begin(), nums.end());
    return nums;
}
```

❌ Time: O(n log n) ➝ due to sorting
✅ OK for small input, **but not optimal**

---

### 🚀 Optimized Approach: Two Pointers (O(n))

**Why?**

* Negative numbers give big squares (e.g., -7² = 49).
* Largest squares are on the **ends** of the array.
* Use two pointers from both sides:

  * Compare absolute values
  * Fill result from the **end** (reverse order)

---

### 👣 Step-by-Step Plan:

1. Create a `result` array of same size.
2. Use two pointers: `left = 0`, `right = n - 1`
3. Start filling `result` from the **back**.
4. At each step:

   * Square `nums[left]` and `nums[right]`
   * Place the **bigger square** at the end
   * Move the pointer (left or right)

---

### 👨‍💻 C++ Code (LeetCode Submission):

```cpp
class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums) {
        int n = nums.size();
        vector<int> result(n);
        int left = 0, right = n - 1;
        int pos = n - 1;

        while (left <= right) {
            int leftSq = nums[left] * nums[left];
            int rightSq = nums[right] * nums[right];

            if (leftSq > rightSq) {
                result[pos--] = leftSq;
                left++;
            } else {
                result[pos--] = rightSq;
                right--;
            }
        }

        return result;
    }
};
```

---

### 🔁 Example (Visual Steps):

Input: `[-7, -3, 2, 3, 11]`

| Step | left | right | Compare   | Place in result | New result           |
| ---- | ---- | ----- | --------- | --------------- | -------------------- |
| 1    | -7   | 11    | 49 vs 121 | 121 at end      | \[..., 121]          |
| 2    | -7   | 3     | 49 vs 9   | 49 at end       | \[..., 49, 121]      |
| 3    | -3   | 3     | 9 vs 9    | 9 at end        | \[..., 9, 49, 121]   |
| 4    | -3   | 2     | 9 vs 4    | 9 at end        | \[..., 9, 9, 49,121] |
| 5    | 2    | 2     | 4 vs 4    | 4 at end        | \[4, 9, 9, 49,121]   |

✅ Final Output: `[4, 9, 9, 49, 121]`

---

### 🧠 Time & Space Complexity:

* **Time:** O(n)
* **Space:** O(n) → new result array

---
