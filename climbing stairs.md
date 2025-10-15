# 🧩 LeetCode 70: Climbing Stairs

## 📘 Problem Description

You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can climb either **1** or **2** steps.  
In how many distinct ways can you climb to the top?

### Example 1:
```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

### Example 2:
```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

---

## 💡 Intuition

This is a **Dynamic Programming** problem similar to the Fibonacci sequence.  
To reach step `n`, you can either come from:

- step `n-1` (by taking one step), or  
- step `n-2` (by taking two steps)

So the total number of ways to reach step `n` is:
```
ways(n) = ways(n-1) + ways(n-2)
```

---

## 🧠 1️⃣ Memoization Approach (Top-Down)

### ✅ Code

```java
import java.util.*;

class SolutionMemo {
    public int climbStairs(int n) {
        int[] dp = new int[n + 1];
        Arrays.fill(dp, -1);
        return solve(n, dp);
    }

    private int solve(int n, int[] dp) {
        if (n <= 2) return n;
        if (dp[n] != -1) return dp[n];
        return dp[n] = solve(n - 1, dp) + solve(n - 2, dp);
    }
}
```

### 🪜 Explanation

- Use a recursive function `solve(n)` that returns the number of ways to reach step `n`.
- Store already computed results in a memoization array `dp[]` to avoid recalculations.
- Base cases:
  - `ways(1) = 1`
  - `ways(2) = 2`

---

## ⚙️ 2️⃣ Tabulation Approach (Bottom-Up)

### ✅ Code

```java
class SolutionTab {
    public int climbStairs(int n) {
        if (n == 1) return 1;
        if (n == 2) return 2;
        
        int[] dp = new int[n];
        dp[0] = 1;
        dp[1] = 2;
        
        for (int i = 2; i < n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        
        return dp[n - 1];
    }
}
```

### 🪜 Explanation

- Build the solution from the base cases upward.
- Each `dp[i]` stores the number of ways to reach step `i+1`.
- Formula: `dp[i] = dp[i-1] + dp[i-2]`.

---

## 🔁 Optimized Version (O(1) Space)

### ✅ Code

```java
class SolutionOptimized {
    public int climbStairs(int n) {
        if (n == 1) return 1;
        int a = 1, b = 2;
        for (int i = 3; i <= n; i++) {
            int c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
}
```

### 💬 Explanation

Instead of storing all values, we only keep the last two results (`a` and `b`).  
This reduces the **space complexity** to `O(1)`.

---

## ⏱️ Complexity Analysis

| Approach | Time Complexity | Space Complexity |
|-----------|----------------|------------------|
| Memoization | O(n) | O(n) |
| Tabulation | O(n) | O(n) |
| Optimized | O(n) | O(1) |

---

## ✅ Example Dry Run (n = 5)

| Step (i) | dp[i] | Explanation |
|-----------|-------|--------------|
| 0 | 1 | One way to reach step 1 |
| 1 | 2 | Two ways to reach step 2 |
| 2 | 3 | 2 + 1 = 3 ways |
| 3 | 5 | 3 + 2 = 5 ways |
| 4 | 8 | 5 + 3 = 8 ways |

👉 **Answer = 8**
