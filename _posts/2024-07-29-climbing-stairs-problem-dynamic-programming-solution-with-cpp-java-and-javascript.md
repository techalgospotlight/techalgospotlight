---
title: "Climbing Stairs Problem: Dynamic Programming Solution with C++, Java, and JavaScript"
excerpt: The climbing stairs problem is a classic dynamic programming problem that involves finding the number of ways to reach the top of a staircase by taking one or two steps at a time. In this article, we will explore the problem statement, constraints, and a dynamic programming solution in C++, Java, and JavaScript.
date: July 29, 2024
layout: post
author: neha
categories:
    - data-structures-algorithms
image: assets/techalgospotlight-dsa-banner.webp
keywords: climbing stairs problem, climbing stairs dynamic programming, climbing stairs problem c++, climbing stairs problem java, climbing stairs problem javascript
published: true
---

The “Climbing Stairs” problem is a classic example in dynamic programming (DP) that illustrates how to break down a problem into simpler subproblems. The challenge is to find the number of distinct ways to reach the top of a staircase with **n** steps, where you can either take 1 step or 2 steps at a time.

Problem Statement
-----------------

Given a staircase with **n** steps, you can either take 1 step or 2 steps to reach the top. The goal is to find out the number of unique ways you can reach the top of the staircase.

### Brute Force Approach

The brute force solution involves exploring all possible ways to reach the top by recursively calculating the number of ways to get to each step. This approach can be visualized as a binary tree where each node represents a step and branches represent the choice of taking 1 or 2 steps.

#### Example

Suppose there are **n = 4** steps. The possible ways to climb are:

```txt
1. 1, 1, 1, 1
2. 1, 1, 2
3. 1, 2, 1
4. 2, 1, 1
5. 2, 2
```


This yields 5 distinct ways.

##### C++ Approach

```cpp
#include <iostream>
using namespace std;

int climbStairs(int n) {
    if (n == 1) return 1;
    if (n == 2) return 2;
    return climbStairs(n - 1) + climbStairs(n - 2);
}

int main() {
    int n = 4;
    cout << "Number of ways to climb " << n << " steps: " << climbStairs(n) << endl;
    return 0;
}
```


##### Time Complexity (TC) and Space Complexity (SC)

*   **TC:** O(2^n) – The time complexity is exponential due to the recursive nature of the solution.
*   **SC:** O(n) – The space complexity is linear, mainly due to the function call stack.

* * *

### Optimal Dynamic Programming Approach

To optimize the solution, we use dynamic programming to store intermediate results and avoid redundant calculations. The idea is to use an array **dp** where **dp[i]** represents the number of ways to reach the **i-th** step.

The recurrence relation is:

>   dp[i] = dp[i - 1] + dp[i - 2]`

#### Example

For **n = 4**:

*   **dp[1] = 1** (only one way: {1})
*   **dp[2] = 2** (two ways: {1,1}, {2})
*   **dp[3] = 3** (three ways: {1,1,1}, {1,2}, {2,1})
*   **dp[4] = 5** (five ways: {1,1,1,1}, {1,1,2}, {1,2,1}, {2,1,1}, {2,2})

##### C++ Approach

```cpp
#include <iostream>
using namespace std;

int climbStairsDP(int n) {
    if (n <= 2) return n;
    int dp[n + 1];
    dp[1] = 1;
    dp[2] = 2;
    for (int i = 3; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}

int main() {
    int n = 4;
    cout << "Number of ways to climb " << n << " steps: " << climbStairsDP(n) << endl;
    return 0;
}
```


##### Time Complexity (TC) and Space Complexity (SC)

*   **TC:** O(n) – The solution iterates through the steps once.
*   **SC:** O(n) – Space complexity is linear due to the `dp` array.

* * *

### Solution in Other Languages

#### Java Solution

```java
public class ClimbStairs {
    public static int climbStairs(int n) {
        if (n <= 2) return n;
        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;
        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }

    public static void main(String[] args) {
        int n = 4;
        System.out.println("Number of ways to climb " + n + " steps: " + climbStairs(n));
    }
}
```


#### JavaScript Solution

```js
function climbStairs(n) {
    if (n <= 2) return n;
    let dp = new Array(n + 1);
    dp[1] = 1;
    dp[2] = 2;
    for (let i = 3; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}

const n = 4;
console.log("Number of ways to climb " + n + " steps: " + climbStairs(n));
```

* * *

Conclusion
----------

The “Climbing Stairs” problem is a straightforward yet powerful illustration of dynamic programming. By breaking down the problem into subproblems and storing intermediate results, we can achieve optimal solutions efficiently. The brute force approach provides a fundamental understanding, while the dynamic programming solution offers an optimized way to solve the problem with significantly reduced time and space complexities.