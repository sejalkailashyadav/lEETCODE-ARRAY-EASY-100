 **LeetCode 905: Sort Array By Parity** in a simple and beginner-friendly way using **C++**, with clear explanation and **LeetCode-submit-ready code**.

---

### ✅ Problem Summary (Easy Words):

You are given an array of integers `nums`.

Your task is to **put all even numbers first**, and then **all odd numbers**.

✔️ The order inside even and odd groups **doesn’t matter**.

---

### 🔍 Example:

#### Input:

```cpp
nums = [3, 1, 2, 4]
```

#### Output:

Any of these are valid:

```
[2, 4, 3, 1]  
[4, 2, 3, 1]  
[2, 4, 1, 3]
```

✅ As long as:

* All even numbers come first
* All odd numbers come after

---

## 💡 Idea: Two-Pointer Fill

We will use **two pointers**:

* One (`i`) starts from beginning
* One (`j`) from end
* Place evens in front, odds at the back

---

### 👨‍💻 C++ Code (LeetCode Submission):

```cpp
class Solution {
public:
    vector<int> sortArrayByParity(vector<int>& nums) {
        vector<int> result(nums.size());
        int i = 0; // for even placement (start)
        int j = nums.size() - 1; // for odd placement (end)

        for (int num : nums) {
            if (num % 2 == 0) {
                result[i++] = num;
            } else {
                result[j--] = num;
            }
        }

        return result;
    }
};
```

---

### 🔁 Visual Example:

Input: `nums = [3, 1, 2, 4]`
We build a result like this:

| Step | num | Even? | result     |
| ---- | --- | ----- | ---------- |
| 1    | 3   | No    | \[ , , ,3] |
| 2    | 1   | No    | \[ , ,1,3] |
| 3    | 2   | Yes   | \[2, ,1,3] |
| 4    | 4   | Yes   | \[2,4,1,3] |

---

### 🧠 Time & Space Complexity:

* **Time:** O(n)
* **Space:** O(n) → new array used

---

### 🔧 Alternate (In-Place Swap):

If you want **in-place solution**, use two-pointer **partitioning**, like this:

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

🧠 **Time:** O(n), **Space:** O(1) (no extra array)

---
