# Fibonacci Number Problem (DP) 📊

The **Fibonacci sequence** is a classic example of Dynamic Programming.  
It is defined as:

```
F(0) = 0
F(1) = 1
F(n) = F(n-1) + F(n-2) for n >= 2
```

The goal is to compute the `n`th Fibonacci number efficiently.

---

## 1️⃣ Top-Down Approach (Memoization)

**Java Code:**

```java
class FibonacciMemoization {
    static int[] memo;

    public static int fib(int n) {
        // Initialize memo array with -1 (not computed)
        memo = new int[n + 1];
        Arrays.fill(memo, -1);
        return helper(n);
    }

    private static int helper(int n) {
        if (n <= 1) return n; // base cases

        if (memo[n] != -1) return memo[n]; // reuse computed value

        // compute and store
        memo[n] = helper(n - 1) + helper(n - 2);
        return memo[n];
    }

    public static void main(String[] args) {
        int n = 10;
        System.out.println("Fibonacci of " + n + " is " + fib(n));
    }
}
```

**How it works:**
1. Recursively computes `fib(n)` using `fib(n-1)` and `fib(n-2)`.  
2. Stores already computed values in the `memo` array.  
3. Avoids redundant calculations (Overlapping Subproblems).  
4. **Time Complexity:** O(n)  
5. **Space Complexity:** O(n) (recursion stack + memo array)  

---

## 2️⃣ Bottom-Up Approach (Tabulation)

**Java Code:**

```java
class FibonacciTabulation {
    public static int fib(int n) {
        if (n <= 1) return n;

        int[] dp = new int[n + 1];
        dp[0] = 0;
        dp[1] = 1;

        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }

        return dp[n];
    }

    public static void main(String[] args) {
        int n = 10;
        System.out.println("Fibonacci of " + n + " is " + fib(n));
    }
}
```

**How it works:**
1. Starts with the smallest subproblems (`dp[0] = 0`, `dp[1] = 1`).  
2. Iteratively builds up the solution to `dp[n]`.  
3. No recursion is used; it is purely iterative.  
4. **Time Complexity:** O(n)  
5. **Space Complexity:** O(n) (can be optimized to O(1) using two variables)  

---

## ✅ Summary

| Method | Time Complexity | Space Complexity | Notes |
|--------|----------------|----------------|-------|
| Memoization (Top-Down) | O(n) | O(n) | Recursive, stores results to avoid recomputation |
| Tabulation (Bottom-Up) | O(n) | O(n) | Iterative, builds solution from small to large |

**Key Points:**
- Memoization is recursive; Tabulation is iterative.  
- Both avoid redundant calculations.  
- Great starting point to learn **Dynamic Programming**.  

---

This file can be placed in your **GitHub DP folder** as a reference for the Fibonacci problem solved using DP.