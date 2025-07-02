## Leetcode 977: Squares of a Sorted Array** step by step in **level-0 beginner-friendly** style.


## 🔸 Problem Summary:

You’re given a **sorted array** (can have **negative numbers**), and you need to:

1. **Square each number**, and
2. **Return the squares in non-decreasing (ascending) order**.

---

## 🔹 Example:

```
Input:  nums = [-4, -1, 0, 3, 10]
Square:         [16, 1, 0, 9, 100]
Sorted Output:  [0, 1, 9, 16, 100]
```

---

## 🔸 Brute Force Approach (Easy)

### ✅ Steps:

1. Square every number.
2. Sort the result.

### 💡 Time: O(n log n) — because of sorting.

### 💡 Space: O(n) — new array.

### ✅ Code:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> sortedSquares(vector<int>& nums) {
    vector<int> result;
    for (int num : nums) {
        result.push_back(num * num);  // Step 1: Square
    }
    sort(result.begin(), result.end());  // Step 2: Sort
    return result;
}
```

---

## 🔸 Optimal Approach (Two Pointer Method) — **O(n)** ✅

### 💡 Why Two Pointers?

Because negative numbers become **large squares**, and largest square may come from **either end** (left or right of array).

---

### ✅ Steps:

1. Use 2 pointers: `left` at beginning, `right` at end.
2. Compare absolute values: `abs(nums[left])` vs `abs(nums[right])`.
3. Bigger square goes to the **end of result array** (fill it **from back**).
4. Move the pointer that gave the bigger square.

---

### 📊 Dry Run:

```
nums = [-7, -3, 2, 3, 11]
result = [_, _, _, _, _]

left = 0 (-7), right = 4 (11)
Compare abs(-7)=7, abs(11)=11 → put 121 at result[4]
right--

Now: result = [_, _, _, _, 121]
Repeat...
```

---

### ✅ Code:

```cpp
#include <iostream>
#include <vector>
using namespace std;

vector<int> sortedSquares(vector<int>& nums) {
    int n = nums.size();
    vector<int> result(n);
    int left = 0, right = n - 1;
    int pos = n - 1;

    while (left <= right) {
        int leftSquare = nums[left] * nums[left];
        int rightSquare = nums[right] * nums[right];

        if (leftSquare > rightSquare) {
            result[pos] = leftSquare;
            left++;
        } else {
            result[pos] = rightSquare;
            right--;
        }
        pos--;
    }

    return result;
}
```

---

## 🔹 Visual Summary:

| Index | Value | Square |
| ----- | ----- | ------ |
| -4    | 16    |        |
| -1    | 1     |        |
| 0     | 0     |        |
| 3     | 9     |        |
| 10    | 100   |        |

Now merge big-to-small from both ends — place largest square at the end and fill backward.

---

## ✅ Final Notes:

* Brute force = easy to write but slow for large arrays.
* Two pointer = smart + fast = **O(n)** time, no sorting!

---

