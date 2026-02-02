Great! Let’s solve Leetcode Problem 941: Valid Mountain Array step by step — beginner-friendly (Level 0) with clear logic, visual example, and C++ code.

---

##  Problem Summary

You are given an array `arr`. Your task is to check whether it forms a mountain shape:

* Length of the array must be at least 3.
* There should be a single peak (maximum point) in the middle.
* Left side must be strictly increasing.
* Right side must be strictly decreasing.

---

## ✅ Example

Let’s break this one down:

### arr = \[0, 3, 2, 1]

It looks like this:
0 → 3 ↑ (peak) → 2 ↓ → 1 ↓
Yes! This is a valid mountain array.

### arr = \[3, 5, 5]

Not valid:

* 5 is repeated → not strictly increasing or decreasing.

### arr = \[2, 1]

Too short → can’t have a peak between → ❌

---

## ✍️ Step-by-step Plan (Logic)

1. Check if size of array is less than 3 → ❌ return false
2. Start from index 0, move up (strictly increasing) → stop at peak
3. Check if peak is not at start or end
4. From peak, move down (strictly decreasing)
5. If you reach the last element after both steps → ✅ return true
   Otherwise → ❌ return false

---

## 📘 Visual Table: arr = \[0, 3, 2, 1]

| Index | Value | Increasing | Decreasing |
| ----- | ----- | ---------- | ---------- |
| 0     | 0     | ✅          |            |
| 1     | 3     | ✅          |            |
| 2     | 2     |            | ✅          |
| 3     | 1     |            | ✅          |

Mountain shape confirmed! ✅

---

## 💻 C++ Code (Simple)

```cpp
#include <vector>
using namespace std;

bool validMountainArray(vector<int>& arr) {
    int n = arr.size();
    if (n < 3) return false;

    int i = 0;

    // walk up
    while (i + 1 < n && arr[i] < arr[i + 1]) {
        i++;
    }

    // peak can't be first or last
    if (i == 0 || i == n - 1) return false;

    // walk down
    while (i + 1 < n && arr[i] > arr[i + 1]) {
        i++;
    }

    return i == n - 1;
}
```

---

## ✅ Test It With

```cpp
vector<int> arr1 = {0, 3, 2, 1};      // true
vector<int> arr2 = {3, 5, 5};         // false
vector<int> arr3 = {2, 1};            // false
```

---

## 🧠 Key Concepts:

* Use a pointer to simulate climbing and then descending a mountain.
* Peak must be in between, not at ends.
* Must strictly go up, then strictly go down.

---
