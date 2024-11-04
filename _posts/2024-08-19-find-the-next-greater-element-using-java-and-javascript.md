---
title: "Find the Next Greater Element using Java and JavaScript"
excerpt: "Learn how to find the next greater element in an array using Java and JavaScript. This guide covers the essential algorithms and code examples to help you solve this problem efficiently."
date: Aug 19, 2024
layout: post
author: neha
categories:
    - data-structures-algorithms
image: assets/techalgospotlight-dsa-banner.webp
keywords: next greater element, next greater element in array, next greater element using stack, next greater element using java, next greater element using javascript
published: true
---

In DSA World, the **Next Greater Element** is the Classic Problem for interviewers and competitive programming. In this problem, we have to find the next greater element of the array that is greater than a given element. As of now, the best way to solve this problem is to Stack and most of these types of data structures are used in stock price analysis, temperature prediction and some cases game development.

* * *

What is the best way to solve the Next Greater Element (NGO)?
-------------------------------------------------------------

The most efficient way to solve this type of problem is **Stack**. Stacks are best because they allow to keep track of every element in **LIFO (Last-In-First-Out)** order. So, this is perfect for comparing array elements and finding the next greater element in the array.

### Why we are not using other data structures?

*   **Arrays** would require a brute-force approach with O(n²) time complexity.
*   **Queues** are FIFO and not suitable for the backtracking nature of the problem.

* * *

Problem Statement
-----------------

Given an array of integer **arr**, for each element in the array, find the next greater element to the right. If no such element exists, return **-1** for that position.

```txt
Input --------
arr = [4, 5, 2, 25] 

Output -------
[5, 25, 25, -1]
```


### Constants

*   The array can have a maximum length of **10^5**.
*   Each element of the array can range between **-10^9** and **10^9**.

Let’s try to understand this problem using pseudo code.

* * *

Pseudo Code
-----------

```js
function findNextGreaterElement(arr):
    stack = empty stack
    result = array of -1's with same length as arr

    for i from 0 to len(arr)-1:
        while stack is not empty and arr[stack.top()] < arr[i]:
            index = stack.pop()
            result[index] = arr[i]
        stack.push(i)

    return result
```


### Step-by-Step Approach

1.  **Initialize an Empty Stack and Result Array:**
    *   The stack will store indices of elements from the array.
    *   The resulting array is initialized with **-1** to indicate no greater element by default.
2.  **Traverse the Array:**
    *   Loop through each element of the array.
    *   For each element, compare it with the element represented by the index at the top of the stack.
3.  **Update the Result Array:**
    *   If the current element is greater than the element indexed at the top of the stack, update the result for the index popped from the stack.
    *   Continue this process until the stack is either empty or the top of the stack is greater than the current element.
4.  **Push Current Index:**
    *   After processing, push the current index onto the stack.
5.  **Return the Result:**
    *   The stack helps track elements that haven’t yet found their Next Greater Element.

* * *

**Hope you understand the approach** 😀

Let’s see how we can implement the **next greater element** in **Java** and **Javascript**.

### Java Approach

```java
import java.util.Stack;

public class NextGreaterElement {
    public static int[] findNextGreaterElement(int[] arr) {
        int n = arr.length;
        int[] result = new int[n];
        Stack<Integer> stack = new Stack<>();

        for (int i = 0; i < n; i++) {
            while (!stack.isEmpty() && arr[stack.peek()] < arr[i]) {
                result[stack.pop()] = arr[i];
            }
            stack.push(i);
        }
        return result;
    }

    public static void main(String[] args) {
        int[] arr = {4, 5, 2, 25};
        int[] result = findNextGreaterElement(arr);
        for (int i : result) {
            System.out.print(i + " ");
        }
    }
}
```


* * *

### JavaScript Approach

```js
function findNextGreaterElement(arr) {
    const n = arr.length;
    const result = new Array(n).fill(-1);
    const stack = [];

    for (let i = 0; i < n; i++) {
        while (stack.length > 0 && arr[stack[stack.length - 1]] < arr[i]) {
            result[stack.pop()] = arr[i];
        }
        stack.push(i);
    }
    return result;
}

// Example usage
const arr = [4, 5, 2, 25];
const result = findNextGreaterElement(arr);
console.log(result.join(" "));
```

* * *

Time Complexity and Space Complexity
------------------------------------

*   **Time Complexity (TC)**: O(n)
    *   Each element is pushed and popped from the stack exactly once, resulting in a linear time complexity.
*   **Space Complexity (SC):** O(n)
    *   The space complexity is due to the stack and the result array, both of which require O(n) space.

* * *

Conclusion
----------

The **Next Greater Element** problem helps us master the Stack data structure. So, Keep Coding 😀 Also, you can find this type of problem in Leecode

*   **Next Greater Element I**
*   **Next Greater Element II**