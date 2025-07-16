[**LeetCode 121: Best Time to Buy and Sell Stock**](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) the same way:

## 🧠 Problem Statement:

> Given an array `prices[]` where `prices[i]` is the price of a stock on day `i`, find the **maximum profit** you can make by buying on one day and selling on another day **after** that.

You can’t sell before you buy.

---

### Example:

```cpp
Input: prices = [7,1,5,3,6,4]  
Output: 5  
Explanation: Buy on day 1 (price=1), sell on day 4 (price=6)
```

---

## 🔹 Step 1: Brute Force Approach

### ✅ Idea:

* Try every pair `(i, j)` where `i < j`
* Calculate `profit = prices[j] - prices[i]`
* Track max profit

### 🧾 C++ Code:

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int maxProfit = 0;
        for (int i = 0; i < prices.size(); i++) {
            for (int j = i + 1; j < prices.size(); j++) {
                int profit = prices[j] - prices[i];
                maxProfit = max(maxProfit, profit);
            }
        }
        return maxProfit;
    }
};
```

⛔ Time: O(n²)
✅ Space: O(1)

---

## 📊 Visual Walkthrough

Let’s use: `prices = [7, 1, 5, 3, 6, 4]`

We check every pair where `buy < sell`.

| Buy Day (i) | Buy Price | Sell Day (j) | Sell Price | Profit | Max Profit So Far |
| ----------- | --------- | ------------ | ---------- | ------ | ----------------- |
| 0           | 7         | 1            | 1          | -6     | 0                 |
| 1           | 1         | 2            | 5          | 4      | 4                 |
| 1           | 1         | 4            | 6          | 5      | ✅ 5 (Best)        |

---

## 🔹 Step 2: Optimized Approach

### ✅ Idea:

* Track the **lowest price** so far as `minPrice`
* At each day, compute `profit = prices[i] - minPrice`
* Track the **maximum profit**

---

### 🔁 Visual Iteration

Input: `[7, 1, 5, 3, 6, 4]`

| Day | Price | Min Price So Far | Profit = price - minPrice | Max Profit |
| --- | ----- | ---------------- | ------------------------- | ---------- |
| 0   | 7     | 7                | 0                         | 0          |
| 1   | 1     | ✅ 1              | 0                         | 0          |
| 2   | 5     | 1                | 4                         | 4          |
| 3   | 3     | 1                | 2                         | 4          |
| 4   | 6     | 1                | ✅ 5                       | ✅ 5        |
| 5   | 4     | 1                | 3                         | 5          |

---

### 🧾 Optimized C++ Code:

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int minPrice = INT_MAX;
        int maxProfit = 0;
        for (int price : prices) {
            minPrice = min(minPrice, price);            // keep lowest price
            maxProfit = max(maxProfit, price - minPrice); // best profit
        }
        return maxProfit;
    }
};
```

⏱ Time: O(n)
📦 Space: O(1)
🔥 Most efficient and LeetCode-accepted.

---

## 🏁 Summary Table:

| Approach                 | Time  | Space | Notes      |
| ------------------------ | ----- | ----- | ---------- |
| Brute Force              | O(n²) | O(1)  | Too slow   |
| Optimized (min tracking) | O(n)  | O(1)  | ✅ Best way |

---

📘 Ready to submit this version on LeetCode:
🔗 [Click here](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

---
