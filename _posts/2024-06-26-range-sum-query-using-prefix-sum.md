---
title: "Range Sum Query Using Prefix Sum"
excerpt: A Range Sum Query is a query for finding all the sum of a subarray or range from a given integer array. This type of query is commonly used in various array algorithms, Specifically in sum computation.
date: June 26, 2024
layout: post
author: neha
categories:
    - data-structures-algorithms
image: assets/techalgospotlight-dsa-banner.webp
keywords: dsa
published: true
---


A **Range Sum Query** is a query for finding all the **sum of a subarray or range** from a given integer array. This type of query is commonly used in various array algorithms, Specifically in sum computation.

In this article, I am going to show everything about range sum queries with examples.

For finding the range sum query, We have to find the first prefix sum of the given array.

What is Prefix Sum
------------------

A prefix sum is an integer array, Where each element at index i is the sum of all elements in the original array from the start-up to the **i** index.

#### Formula of Prefix Sum

> **prefix_sum[i] = prefix_sum[i−1] + arr[i]**

#### Prefix Sum Program in Java

```java
public class PrefixSum {
    public static void main(String[] args) {
        // Example array
        int[] arr = {1, 2, 3, 4, 5};
        
        // Compute the prefix sum array
        int[] prefixSum = computePrefixSum(arr);
        
        // Print the prefix sum array
        for (int sum : prefixSum) {
            System.out.print(sum + " ");
        }
    }

    // Method to compute prefix sum
    public static int[] computePrefixSum(int[] arr) {
        int n = arr.length;
        int[] prefixSum = new int[n];
        
        // Initialize the first element of prefix sum array
        prefixSum[0] = arr[0];
        
        // Compute the prefix sum for each element
        for (int i = 1; i < n; i++) {
            prefixSum[i] = prefixSum[i - 1] + arr[i];
        }
        
        return prefixSum;
    }
}
```


With the help of prefix sum, We can find range sum queries of any array with **optimal time and space complexity**.

* * *

#### Range Sum Query Program in Java using Prefix Sum


```java
public class RangeSumQuery {
    public static void main(String[] args) {
        // Example array
        int[] arr = {1, 2, 3, 4, 5};
        
        // Compute the prefix sum array
        int[] prefixSum = computePrefixSum(arr);
        
        // Example range sum queries
        System.out.println("Sum of elements from index 1 to 3: " + rangeSum(prefixSum, 1, 3));
        System.out.println("Sum of elements from index 0 to 4: " + rangeSum(prefixSum, 0, 4));
    }

    // Method to compute prefix sum
    public static int[] computePrefixSum(int[] arr) {
        int n = arr.length;
        int[] prefixSum = new int[n];
        
        // Initialize the first element of prefix sum array
        prefixSum[0] = arr[0];
        
        // Compute the prefix sum for each element
        for (int i = 1; i < n; i++) {
            prefixSum[i] = prefixSum[i - 1] + arr[i];
        }
        
        return prefixSum;
    }

    // Method to compute range sum using prefix sum array
    public static int rangeSum(int[] prefixSum, int l, int r) {
        if (l == 0) {
            return prefixSum[r];
        } else {
            return prefixSum[r] - prefixSum[l - 1];
        }
    }
}
```


#### Output

```
Sum of elements from index 1 to 3: 9
Sum of elements from index 0 to 4: 15
```

##### Time Complexity

*   **Prefix Sum – O(n)**
*   **Range Sum – O(1)**

##### Space Complexity

*   **Prefix Sum – O(n)**

* * *

### Conclusion

In the Upcoming article, we will see more about prefix sum and range sum queries and their requirements in algorithms.