# Fibonacci Number Problem (DP) 📊

The **Fibonacci sequence** is a classic example of Dynamic Programming.  
It is defined as:


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
