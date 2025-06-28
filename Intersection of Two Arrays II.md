## 🔍 Problem Summary:

You're given two arrays `nums1` and `nums2`.
👉 Return an array containing their **intersection** — each number should appear **as many times** as it appears in **both arrays**.

✅ Order doesn’t matter.

---

### 🧠 Example 1:

**Input:** `nums1 = [1,2,2,1]`, `nums2 = [2,2]`
**Output:** `[2,2]`

---

### 🧠 Example 2:

**Input:** `nums1 = [4,9,5]`, `nums2 = [9,4,9,8,4]`
**Output:** `[4,9]` or `[9,4]`

---

## 🛠️ 1. Brute Force Approach (Level-0)

### 💡 Logic:

* Use a `visited` array to mark used elements in `nums2`.
* For each element in `nums1`, search linearly in `nums2`.

### ⏱️ Time: O(n \* m)

📦 Space: O(n) for result

Too slow for large input, not recommended.

---

## ⚡ 2. Optimized Approach using Hash Map (Best for general case)

### 💡 Logic:

* Count frequencies of elements in `nums1` using `unordered_map`.
* For each element in `nums2`, check if it's in the map and count > 0.

  * If yes → add to result and decrease count.

---

### ✅ Time: O(n + m)

📦 Space: O(min(n, m)) → Map only stores one array's data

---

### 🧾 Code (C++ using Hash Map):

```cpp
#include <vector>
#include <unordered_map>
using namespace std;

class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        unordered_map<int, int> freq;
        vector<int> result;

        // Count frequency in nums1
        for (int num : nums1) {
            freq[num]++;
        }

        // Match from nums2
        for (int num : nums2) {
            if (freq[num] > 0) {
                result.push_back(num);
                freq[num]--; // Decrease count
            }
        }

        return result;
    }
};
```

---

## 🔄 3. Follow-up Optimization (Sorted Arrays)

If arrays are **sorted**, use **Two Pointers** approach:

### 💡 Logic:

* Use two indices, `i` and `j`, to walk through `nums1` and `nums2`
* If elements match → add to result, move both pointers
* Else move the smaller one

---

### ⏱️ Time: O(n + m)

📦 Space: O(1) extra if not counting result array

---

### 🧾 Code (Sorted Arrays):

```cpp
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());

        int i = 0, j = 0;
        vector<int> result;

        while (i < nums1.size() && j < nums2.size()) {
            if (nums1[i] == nums2[j]) {
                result.push_back(nums1[i]);
                i++; j++;
            }
            else if (nums1[i] < nums2[j]) {
                i++;
            }
            else {
                j++;
            }
        }

        return result;
    }
};
```

---

## ⚙️ Advanced Follow-Up Questions Answered:

### Q1. If arrays are sorted?

✅ Use **two pointers** → Faster, avoids hashmap

### Q2. If `nums1` is much smaller?

✅ Build hash map from smaller array → less memory used

### Q3. If `nums2` is on disk and memory-limited?

✅ Stream `nums2` in chunks, and:

* Store `nums1` in a map
* For each chunk of `nums2`, process and match

---

### ✅ Summary:

| Scenario                   | Best Approach     | Time | Space  |
| -------------------------- | ----------------- | ---- | ------ |
| General case               | Hash Map          | O(n) | O(n)   |
| Arrays are sorted          | Two pointers      | O(n) | O(1)   |
| `nums1` small              | Hash Map on small | O(n) | O(min) |
| `nums2` on disk (streamed) | Hash + Streaming  | O(n) | O(min) |

---
