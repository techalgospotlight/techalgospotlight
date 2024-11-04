---
title: "Find the Closest Min-Max using Javascript"
excerpt: The Min Max algorithm efficiently finds the minimum (min) and maximum (max) values in an array of numbers. This approach involves traversing the array while keeping track of the current minimum and maximum values encountered..
date: July 12, 2024
layout: post
author: neha
categories:
    - data-structures-algorithms
image: assets/techalgospotlight-dsa-banner.webp
keywords: dsa, min max using js
published: true
---

The Min Max algorithm efficiently finds the minimum (min) and maximum (max) values in an array of numbers. This approach involves traversing the array while keeping track of the current minimum and maximum values encountered.

Problem Description
-------------------

Given an array A, find the size of the smallest subarray such that it contains at least one occurrence of the maximum value of the array and at least one occurrence of the minimum value of the array.

### Problem Constraints

### Input Format

```txt
First and only argument is vector A
```

### Output Format

```txt
Return the length of the smallest subarray which has at least one occurrence of minimum and maximum element of the array.
```

### Example Input / Output

```txt
Input 1:
A = [1, 3, 2]
Input 2:
A = [2, 6, 1, 6, 9]

Output 1:
2
Output 2:
3
```

### Example Explanation

```txt
Explanation 1:
Take the 1st and 2nd elements as they are the minimum and maximum elements respectievly.

Explanation 2:
Take the last 3 elements of the array.
```

* * *

### Program Steps

Steps to Implement the MinMax Algorithm:

1.  **Initialization**
    *   Start by initializing two variables, **min** and **max**, with the values of the first element in the array.
2.  **Iterate through the Array**
    *   Traverse the array from the second element to the last element.
    *   For each element:
        *   Compare it with the current **min** value. If the element is smaller than **min**, update **min** to be this element.
        *   Compare it with the current **max** value. If the element is larger than **max**, update **max** to be this element.
3.  **Result**
    *   After traversing the entire array, **min** will contain the smallest value and **max** the largest value.
4.  **Edge Cases**
    *   Handle arrays with zero elements by returning appropriate values or indicators as needed.

* * *

### JavaScript Output

```js
function findMinMax(arr) {
    if (arr.length === 0) {
        return { min: null, max: null };
    }

    let min = arr[0];
    let max = arr[0];

    for (let i = 1; i < arr.length; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
        if (arr[i] > max) {
            max = arr[i];
        }
    }

    return { min: min, max: max };
}

// Example usage:
const array = [3, 5, 1, 8, 2, 9, -1];
const result = findMinMax(array);
console.log(`Min: ${result.min}, Max: ${result.max}`);  // Output: Min: -1, Max: 9
```