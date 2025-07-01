### ✅ Problem Summary (Simple Language):

You are given an array of numbers that should contain numbers from **1 to n**.
But:

* One number is **repeated twice** (duplicate)
* One number is **missing**

👉 Return both numbers like this:
**\[duplicate, missing]**

---

### 🔍 Example:

#### Input:

```
nums = [1, 2, 2, 4]
```

#### Step-by-step:

* Numbers should be: **\[1, 2, 3, 4]**
* But 2 is repeated ➝ ✅ **duplicate = 2**
* And 3 is missing ➝ ❌ **missing = 3**

✔️ Output → `[2, 3]`

---

## 🔧 Step-by-Step Approach (Using Hash Map)

We’ll use a **map** (or unordered\_map) to count how many times each number appears.

### Steps:

1. Count how many times each number occurs using a `map`.
2. Find:

   * The number with count `2` ➝ this is the **duplicate**
   * The number from `1 to n` that is **not in map** ➝ this is the **missing**

---

### 👨‍💻 C++ Code:

```cpp
#include <iostream>
#include <vector>
#include <map>
using namespace std;

vector<int> findErrorNums(vector<int>& nums) {
    map<int, int> count;
    for (int num : nums) {
        count[num]++;
    }

    int duplicate = -1, missing = -1;
    for (int i = 1; i <= nums.size(); i++) {
        if (count[i] == 2) {
            duplicate = i;
        } else if (count[i] == 0) {
            missing = i;
        }
    }

    return {duplicate, missing};
}

int main() {
    vector<int> nums = {1, 2, 2, 4};
    vector<int> result = findErrorNums(nums);
    cout << "[" << result[0] << ", " << result[1] << "]" << endl;
    return 0;
}
```

---

### 🧠 Visual Map (for nums = \[1, 2, 2, 4]):

| Number | Count |             |
| ------ | ----- | ----------- |
| 1      | 1     |             |
| 2      | 2     | ✅ Duplicate |
| 3      | 0     | ❌ Missing   |
| 4      | 1     |             |

---

### ✅ Final Output:

```
[2, 3]
```

---

### 🔁 Test Case 2:

```cpp
vector<int> nums = {1, 1};
// Expected Output: [1, 2]
```

---

Let me know if you want the **optimized solution** (without map), or continue to the **next problem**.
Let's solve **LeetCode 645: Set Mismatch** step-by-step in **Level-0 Beginner Style** using **C++**, with a clear **explanation**, **visual steps**, and **code**.

---

### ✅ Problem Summary (Simple Language):

You are given an array of numbers that should contain numbers from **1 to n**.
But:

* One number is **repeated twice** (duplicate)
* One number is **missing**

👉 Return both numbers like this:
**\[duplicate, missing]**

---

### 🔍 Example:

#### Input:

```
nums = [1, 2, 2, 4]
```

#### Step-by-step:

* Numbers should be: **\[1, 2, 3, 4]**
* But 2 is repeated ➝ ✅ **duplicate = 2**
* And 3 is missing ➝ ❌ **missing = 3**

✔️ Output → `[2, 3]`

---

## 🔧 Step-by-Step Approach (Using Hash Map)

We’ll use a **map** (or unordered\_map) to count how many times each number appears.

### Steps:

1. Count how many times each number occurs using a `map`.
2. Find:

   * The number with count `2` ➝ this is the **duplicate**
   * The number from `1 to n` that is **not in map** ➝ this is the **missing**

---

### 👨‍💻 C++ Code:

```cpp
#include <iostream>
#include <vector>
#include <map>
using namespace std;

vector<int> findErrorNums(vector<int>& nums) {
    map<int, int> count;
    for (int num : nums) {
        count[num]++;
    }

    int duplicate = -1, missing = -1;
    for (int i = 1; i <= nums.size(); i++) {
        if (count[i] == 2) {
            duplicate = i;
        } else if (count[i] == 0) {
            missing = i;
        }
    }

    return {duplicate, missing};
}

int main() {
    vector<int> nums = {1, 2, 2, 4};
    vector<int> result = findErrorNums(nums);
    cout << "[" << result[0] << ", " << result[1] << "]" << endl;
    return 0;
}
```

---

### 🧠 Visual Map (for nums = \[1, 2, 2, 4]):

| Number | Count |             |
| ------ | ----- | ----------- |
| 1      | 1     |             |
| 2      | 2     | ✅ Duplicate |
| 3      | 0     | ❌ Missing   |
| 4      | 1     |             |

---

### ✅ Final Output:

```
[2, 3]
```

---

### 🔁 Test Case 2:

```cpp
vector<int> nums = {1, 1};
// Expected Output: [1, 2]
```

---
