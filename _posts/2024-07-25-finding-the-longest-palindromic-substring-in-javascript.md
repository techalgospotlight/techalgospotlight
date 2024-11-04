---
title: "Finding the Longest Palindromic Substring in JavaScript"
excerpt: "Learn how to find the longest palindromic substring in a given string using JavaScript. This guide covers the problem statement, approach, and code implementation to help you solve this problem efficiently."
layout: post
date: July 25, 2024
author: neha
categories:
    - data-structures-algorithms
image: assets/techalgospotlight-dsa-banner.webp
keywords: dsa, palindromic substring, javascript, dsa tutorial, javascript programming language, javascript for beginners
published: true
---

A palindrome is a sequence that reads the same backwards as forward. Given a string, identifying the longest palindromic substring within it is a common problem in computer science. In this article, we’ll explore an efficient approach to solve this problem using JavaScript. The algorithm leverages the concept of expanding around potential centres of palindromes to find the longest one.

Problem Description
-------------------

Given a string **A** of size **N**, we need to find and return the longest palindromic substring in **A**. If multiple such substrings exist, we should return the one that occurs first (with the least starting index).

### Constraints

```plaintext
1≤N≤6000
```

### Input Format

```plaintext
The first and only argument is a string A.
```

### Output Format

```plaintext
Return a string denoting the longest palindromic substring of string A.
```
* * *

Solution Approach
-----------------

The algorithm uses the concept of expanding around the center. Each character in the string can be considered as the center of a palindrome. Additionally, the center of a palindrome can also be between two characters for even-length palindromes. We expand around these centers to find the longest palindromic substring.

### Steps

*   **Initialize Variables**: Track the start and end indices of the longest palindromic substring found.
*   **Odd-Length Palindromes**: For each character, consider it as the center of an odd-length palindrome and expand outward as long as the characters on both sides are equal.
*   **Even-Length Palindromes**: For each pair of consecutive characters, consider them as the center of an even-length palindrome and expand outward similarly.
*   **Update Longest Palindrome**: If a longer palindrome is found during the expansion, update the start and end indices.
*   **Return the Longest Palindromic Substring**: Slice the string using the recorded indices to get the longest palindromic substring.

* * *

JavaScript Implementation
-------------------------

```js
function longestPalindromicSubstring(A) {
    let maxPalindrone = 1;
    let start = 0;
    let end = 1;

    // for each character in A, check if it is the center of a palindrome of odd length
    for (let i = 1; i < A.length - 1; i++) {
        let length = 0;
        let s = i - 1;
        let e = i + 1;

        // check if the character is the center of a palindrome of odd length
        // and expand the palindrome to the left and right as long as the characters match
        while (s >= 0 && e < A.length && A[s] === A[e]) {
            length += 2;
            s--;
            e++;
        }

        // if the length of the palindrome is greater than the current max, update the max
        if (maxPalindrone < length) {
            maxPalindrone = length;
            start = s + 1;
            end = e;
        }
    }

    // for each character in A, check if it is the center of a palindrome of even length
    for (let i = 0; i < A.length - 1; i++) {

        // check if the character is the center of a palindrome of even length
        if (A[i] === A[i + 1]) {
            let length = 2;
            let s = i - 1;
            let e = i + 2;

            // expand the palindrome to the left and right as long as the characters match
            while (s >= 0 && e < A.length && A[s] === A[e]) {
                length += 2;
                s--;
                e++;
            }

            // if the length of the palindrome is greater than the current max, update the max
            if (maxPalindrone < length) {
                maxPalindrone = length;
                start = s + 1;
                end = e;
            }
        }
    }

    return A.slice(start, end);
}
```


* * *

Explanation of the Code
-----------------------

*   **Initialization**: maxPalindrone is initialized to 1 because the smallest possible palindrome is a single character. start and end track the indices of the longest palindrome found.
*   **Odd-Length Palindromes**: The first loop iterates over each character (excluding the first and last to avoid boundary issues) and expands outward while the characters on both sides are equal.
*   **Even-Length Palindromes**: The second loop checks for even-length palindromes by considering pairs of consecutive characters as the center.
*   **Updating Maximum Length**: Whenever a longer palindrome is found, start and end are updated to reflect the new longest palindrome indices.
*   **Return Statement**: Finally, the function returns the substring from start to end.

* * *

Conclusion
----------

The algorithm efficiently finds the longest palindromic substring in a given string by expanding around potential centers. This approach ensures that we check both odd and even-length palindromes, covering all possible cases. The implementation is straightforward and runs in **O(N2)O(N^2)O(N2)** time complexity, which is optimal for the given constraint.