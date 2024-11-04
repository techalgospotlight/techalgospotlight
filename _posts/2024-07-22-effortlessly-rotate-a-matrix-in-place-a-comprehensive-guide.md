---
title: "Effortlessly Rotate a Matrix in Place: A Comprehensive Guide"
excerpt: "Learn how to rotate a matrix by 90 degrees clockwise in place without using additional memory. This guide provides a step-by-step explanation and example code to help you understand the rotation process."
layout: post
date: July 22, 2024
author: neha
categories:
    - data-structures-algorithms
image: assets/techalgospotlight-dsa-banner.webp
keywords: rotate matrix, rotate matrix by 90 degrees, rotate matrix in place, rotate matrix clockwise
published: true
---

Rotating a matrix by 90 degrees clockwise is a common problem in computer science and technical interviews. This problem can be particularly interesting because the goal is to perform the rotation in place, without using additional memory for a new matrix. In this guide, we will explore how to achieve this with a clear explanation and example code.

Problem Description
-------------------

You are given an n x n 2D matrix **A** representing an image. Your task is to rotate the image clockwise at 90 degrees in place. If you use an additional array, you will only receive partial credit.

### Problem Constraints

```txt
1≤n≤1000
```

### Input Format

```txt
A 2D matrix A of integers
```

### Output Format

```txt
The 2D rotated matrix
```

* * *

### Example Explanation

After rotating the matrix by 90 degrees:

*   1 goes to position 2
*   2 goes to position 4
*   4 goes to position 3
*   3 goes to position 1

#### Step-by-Step Solution

##### Step 1: Transpose the Matrix

Transposing a matrix means converting its rows into columns and columns into rows. This can be done by swapping elements across the main diagonal (top-left to bottom-right diagonal).

##### Step 2: Reverse Each Row

Once the matrix is transposed, the next step is to reverse each row. This will effectively rotate the matrix by 90 degrees clockwise.

* * *

### Example Code

Here’s a JavaScript function to perform the rotation:

```js
function rotateMatrix(A) {
    const n = A.length;

    // Step 1: Transpose the matrix
    for (let i = 0; i < n; i++) {
        for (let j = i; j < n; j++) {
            let temp = A[i][j];
            A[i][j] = A[j][i];
            A[j][i] = temp;
        }
    }

    // Step 2: Reverse each row
    for (let i = 0; i < n; i++) {
        A[i].reverse();
    }

    return A;
}

// Example usage:
let matrix = [
    [1, 2],
    [3, 4]
];

console.log(rotateMatrix(matrix));
```


* * *

### Explanation of the Code

**Transpose the Matrix:**

*   Loop through the matrix using two nested loops.
*   Swap elements **A[i][j]** and **A[j][i]** to transpose the matrix.

**Reverse Each Row:**

*   Use the built-in **reverse()** method to reverse each row in the transposed matrix.

**Return the Rotated Matrix:**

*   After transposing and reversing each row, the matrix is rotated by 90 degrees clockwise.

* * *

Conclusion
----------

Rotating a matrix in place is a valuable skill that showcases your understanding of array manipulation and in-place algorithms. By transposing the matrix and then reversing each row, you can achieve the desired rotation without using extra space. Practice this method to enhance your problem-solving abilities in technical interviews and coding challenges.