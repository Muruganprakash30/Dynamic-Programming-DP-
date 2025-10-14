# Dynamic Programming (DP) 📊

Dynamic Programming (DP) is a **powerful problem-solving technique** used to solve **complex problems efficiently** by breaking them down into smaller subproblems and **storing the results** to avoid redundant computations. DP is widely used in competitive programming, interviews, and optimization problems.

---

## 🔑 Key Concepts

1. **Optimal Substructure**  
   A problem has an optimal substructure if the solution to the problem can be **constructed from solutions of its subproblems**.  

   Example: Fibonacci sequence  

2. **Overlapping Subproblems**  
A problem has overlapping subproblems if **the same subproblem is solved multiple times**.  

Example: Fibonacci recursion calculates F(3) multiple times.

3. **Memoization** (Top-Down)  
- Solve the problem **recursively**.  
- **Store results** of subproblems in a table or array.  
- Reuse stored results instead of recomputing.

4. **Tabulation** (Bottom-Up)  
- Solve **smaller subproblems first**.  
- Build the solution **iteratively** using a table (array).  
- Often more efficient than recursion.

---

## 🛠 Types of DP

| Type | Approach | Example Problems |
|------|----------|-----------------|
| **1D DP** | Array of size `n` | Fibonacci, Climbing Stairs, Min Cost Climbing Stairs |
| **2D DP** | Matrix/table | Longest Common Subsequence, Edit Distance, Unique Paths |
| **Decision DP** | Choose optimal at each step | House Robber, Coin Change, Knapsack |
| **State DP** | Use multiple parameters to represent state | Dungeon Game, Stock Trading with cooldown |

---

## 📝 How to Solve DP Problems

1. **Identify Subproblems**  
Break the main problem into smaller overlapping subproblems.

2. **Find Recurrence Relation**  
Determine how the solution of a subproblem relates to smaller subproblems.

3. **Decide Storage Approach**  
- Memoization (top-down recursion)  
- Tabulation (bottom-up iterative)

4. **Implement Base Cases**  
Handle smallest subproblems directly.

5. **Fill the Table / Recurse**  
Solve all subproblems and store their results.

6. **Return Final Solution**  
Usually the result is at the last index or computed recursively.

---

## 📌 Tips

- Start with **easy 1D problems** like Fibonacci and Climbing Stairs.  
- Visualize **the DP table or array** to understand computation flow.  
- Once comfortable, move to **2D DP and decision DP** problems.  
- Practice is key! Solve problems from **LeetCode, GeeksforGeeks, and HackerRank**.

---

This README can serve as a **guide for your DP folder** on GitHub, where you can add solved DP problems with both **Memoization and Tabulation** implementations.
