---
title: "Chocolate Distribution Problem: Maximum and Minimum Chocolates"
excerpt: "Learn how to solve the chocolate distribution problem to maximize and minimize the number of chocolates distributed among students. This guide covers the essential algorithms and code examples to help you solve this problem efficiently."
date: Aug 20, 2024
layout: post
author: neha
categories:
    - data-structures-algorithms
image: assets/techalgospotlight-dsa-banner.webp
keywords: chocolate distribution problem, chocolate distribution problem maximum, chocolate distribution problem minimum, chocolate distribution problem using sorting
published: true
---


The **Chocolate Distribution Problem** is a classic algorithmic challenge that involves distributing chocolate packets among students to minimize the difference between the **maximum and minimum chocolates** received. This problem is essential in various applications, such as resource allocation and load balancing. In this article, we will explore the efficient solution to the Chocolate Distribution Problem using Sort.

* * *

Problem Statement
-----------------

Given an array of integers representing the number of chocolates in each packet and a number **'m'** representing the number of students, find the minimum difference between the **maximum** and **minimum** chocolates received by any student after **distributing** the chocolates. The constraints include ensuring each student receives exactly one packet and minimising the difference between the maximum and minimum chocolates.

```txt
Input: 
arr[] = {12, 4, 7, 9, 2, 23, 25, 41, 30, 40, 28, 42, 30, 44, 48, 43, 50}, m = 7

Output: 
Minimum difference is 10
```


Algorithm/Implementation
------------------------

The efficient solution involves sorting the array of chocolate packets and finding the **subarray** of size **'m'** with the minimum difference between the **last** and **first** elements.

1.  Sort the array of chocolate packets in ascending order.
2.  Initialize a variable ‘min\_diff’ to store the minimum difference and set it to the maximum possible integer value.
3.  Iterate through the array and find the subarray of size ‘m’ with the minimum difference between the last and first elements.
4.  Update ‘min\_diff’ if a smaller difference is found.
5.  Return ‘min\_diff’ as the minimum difference between the maximum and minimum chocolates any student receives.

* * *

Java Implementation:
--------------------

```java
public class ChocolateDistribution {
    public static int chocolateDistribution(int arr[], int m) {
        // Check base cases
        if (arr.length == 0 || m == 0) {
            return 0;
        }

        // Sort the array
        Arrays.sort(arr);

        // Check if there are enough packets for the given number of students
        if (arr.length - 1 < m) {
            return -1;
        }

        // Initialize minimum difference
        int min_diff = Integer.MAX_VALUE;

        // Iterate through the array
        for (int i = 0; i < arr.length; i++) {
            int nextWindow = i + m - 1;
            if (nextWindow >= arr.length) {
                break;
            }
            int diff = arr[nextWindow] - arr[i];
            min_diff = Math.min(min_diff, diff);
        }

        return min_diff;
    }
}
```


* * *

Explanation
-----------

The algorithm sorts the array and finds the subarray of size **7** with the minimum difference between the last and first elements. The **subarray {30, 30, 40, 41, 42, 43, 44}** has a minimum difference of **10**.

* * *

Complexity Analysis
-------------------

### Time Complexity

*   **O(N\*log(N))**, where N is the number of chocolate packets.

### Space Complexity

*   **O(1)**, as only a constant amount of space is used.

### Trade-offs

*   The efficient solution involves sorting the array, which takes **O(N\*log(N))** time. However, this allows for a **linear-time search** for the minimum difference subarray.

* * *

Conclusion
----------

The Chocolate Distribution Problem is a classic algorithmic challenge that can be solved efficiently using sorting and iteration. The solution has a time complexity of **O(N\*log(N))** and space complexity of **O(1)**. Understanding this problem and its solution can help with resource allocation and load balancing in various applications.