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

The problem is similar to finding the **nth Fibonacci number**.  
To reach step `n`, you can come from either:

- step `n-1` (by taking one step), or  
- step `n-2` (by taking two steps)

So the total number of ways to reach `n` is:

```
ways(n) = ways(n-1) + ways(n-2)
```

---

## 🧠 Code (Tabulation - Bottom Up)

```java
class Solution {
    public int climbStairs(int n) {
        if(n==1)return 1;
        if(n==2)return 2;
        int dp[] = new int[n];
        dp[0]=1;
        dp[1]=2;
        for(int i=2;i<n;i++)
        {
           dp[i] = dp[i-1]+dp[i-2];  
        }
        return dp[n-1];
    }
}
```

---

## 🪜 Step-by-Step Explanation

1. **Base Cases**
   - If `n == 1`, only one way: (1)
   - If `n == 2`, two ways: (1+1) or (2)

2. **DP Array Initialization**
   - Create an array `dp` of size `n`.
   - `dp[0] = 1` (ways to reach step 1)
   - `dp[1] = 2` (ways to reach step 2)

3. **Filling the DP Array**
   - Start from index 2 up to `n-1`
   - For each step `i`, calculate total ways:
     ```
     dp[i] = dp[i-1] + dp[i-2]
     ```

4. **Return the Answer**
   - The final answer is `dp[n-1]`, the number of ways to reach the nth step.

---

## ⏱️ Complexity Analysis

| Type | Complexity |
|------|-------------|
| Time | O(n) |
| Space | O(n) |

---

## ✅ Example Dry Run

Let’s take **n = 5**:

| Step (i) | dp[i] | Explanation |
|-----------|-------|--------------|
| 0 | 1 | One way to reach step 1 |
| 1 | 2 | Two ways to reach step 2 |
| 2 | 3 | 2 + 1 = 3 ways |
| 3 | 5 | 3 + 2 = 5 ways |
| 4 | 8 | 5 + 3 = 8 ways |

👉 **Answer = 8**

---

## 🔁 Optimized Version (O(1) Space)

```java
class Solution {
    public int climbStairs(int n) {
        if(n==1)return 1;
        int a = 1, b = 2;
        for(int i=3;i<=n;i++){
            int c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
}
```
