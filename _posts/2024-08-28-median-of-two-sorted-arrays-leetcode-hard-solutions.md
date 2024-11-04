---
title: "Median of Two Sorted Arrays – LeetCode Hard Solutions"
excerpt: "Learn how to find the median of two sorted arrays without merging them using Python. This guide covers the problem statement, approaches, and code solutions to help you solve this problem efficiently."
date: Aug 28, 2024
layout: post
author: neha
categories:
    - data-structures-algorithms
image: assets/sticky-post.jpg
keywords: median of two sorted arrays, median of two sorted arrays leetcode, median of two sorted arrays python 
published: true
tags: sticky
---

Are you tired of being average? Well, data analysis has got you covered! Meet the median, the ultimate middle child of statistics. It’s like the cool cousin who shows up to family reunions and says, “Hey, I’m not the highest, nor the lowest, but I’m here, and I’m representative!” **LeetCode’s 4th Hard problem, “Median of Two Sorted Arrays**,” is like the median’s coming-out party – and you’re invited!

* * *

Problem Statement
-----------------

* * *

### Finding the Median of Two Sorted Arrays

Given two sorted arrays **nums1** and **nums2** of size **m** and **n** respectively, return the median of the **two sorted arrays.**

### Constraints:

*   0 <= m, n <= 1000
*   1 <= m + n <= 2000
*   -106 <= nums1[i], nums2[i] <= 106

### What’s the Catch?

*   The arrays are **sorted**, but merging them would be inefficient.
*   The median might not be an **integer**.
*   It would be best if you found a solution that’s faster than **O((m+n) log(m+n))**.

### Your Mission:

Find the **median of two sorted arrays without merging** them, optimizing for time and space complexity.

#### Are you Excited?

* * *

Approaches and Solutions
------------------------

* * *

### A. Brute Force Approach (Merging and Sorting)

The brute force approach involves **merging the two sorted arrays** into one and then finding the median.

#### Code Implementation (Python):

```py
def findMedianSortedArrays(nums1, nums2):
    # Merge and sort the arrays
    merged = sorted(nums1 + nums2)
    
    # Find the median
    length = len(merged)
    if length % 2 == 0:
        return (merged[length // 2 - 1] + merged[length // 2]) / 2
    else:
        return merged[length // 2]
```


#### Explanation:

1.  Merge **nums1** and **nums2** into a single array **merged**.
2.  Sort **merged** in ascending order.
3.  Calculate the median based on the length of **merged**.

#### Why This Approach is Not Ideal:

1.  **Time Complexity:** O((m+n) log(m+n)) due to sorting, where m and n are the lengths of nums1 and nums2.
2.  **Space Complexity:** O(m+n) for storing the merged array.
3.  **Inefficiency:** Merging and sorting large arrays can be slow.

#### Limitations:

1.  This approach is impractical for large inputs.
2.  It doesn’t utilize the fact that the input arrays are already sorted.

* * *

### B. Optimized Approach (Binary Search)

The optimized approach leverages **binary search** to find the median without merging the arrays.

#### **Key Insights:**

1.  The median is the middle element in the combined sorted array.
2.  We can find the median by partitioning the combined array into two halves.

#### Code Implementation (Python):

```py
def findMedianSortedArrays(nums1, nums2):
    if len(nums1) > len(nums2):
        nums1, nums2 = nums2, nums1
    
    x, y = len(nums1), len(nums2)
    start = 0
    end = x
    
    while start <= end:
        partitionX = (start + end) // 2
        partitionY = (x + y + 1) // 2 - partitionX
        
        maxLeftX = float('-inf') if partitionX == 0 else nums1[partitionX - 1]
        minRightX = float('inf') if partitionX == x else nums1[partitionX]
        
        maxLeftY = float('-inf') if partitionY == 0 else nums2[partitionY - 1]
        minRightY = float('inf') if partitionY == y else nums2[partitionY]
        
        if maxLeftX <= minRightY and maxLeftY <= minRightX:
            if (x + y) % 2 == 0:
                return (max(maxLeftX, maxLeftY) + min(minRightX, minRightY)) / 2.0
            else:
                return max(maxLeftX, maxLeftY)
        
        elif maxLeftX > minRightY:
            end = partitionX - 1
        
        else:
            start = partitionX + 1
    
    # Return statement for edge cases or errors
    return None  # or raise ValueError("Invalid input")
```


#### Explanation:

1.  Ensure nums1 is the smaller array.
2.  Initialize start = 0 and end = nums1.length.
3.  Calculate the partition point partitionX = (start + end) / 2.
4.  Calculate the corresponding partition point partitionY = (nums1.length + nums2.length + 1) / 2 - partitionX.
5.  Compare elements at partitionX and partitionY.
6.  Adjust start and end based on the comparison.
7.  Repeat steps 3-6 until start <= end.

#### Time & Space Complexity:

*   **Time Complexity:** O(log(min(m,n)))
*   **Space Complexity:** O(1)

#### Advantages:

1.  Efficient for large inputs.
2.  Utilizes the fact that input arrays are sorted.

**The optimized approach using binary search efficiently finds the median without merging the arrays.**

* * *

Conclusion
----------

* * *

### Finding Medians in Sorted Arrays: Key Takeaways and Next Steps

In this article, we explored the crucial problem of finding medians in sorted arrays. We discussed:

#### Key Takeaways:

1.  **Importance of Medians**: Understanding data distribution and central tendency.
2.  **Brute Force Approach**: Merging and sorting arrays, with O((m+n) log(m+n)) time complexity.
3.  **Optimized Approach**: Binary search, achieving O(log(min(m,n))) time complexity.
4.  **Code Implementations**: Efficient solutions in Python.

#### What’s Next?

1.  **Practice**: Solve similar problems on LeetCode, HackerRank, and other platforms.
2.  **Real-World Applications**: Apply median-finding skills in data analysis, machine learning, and database optimization.
3.  **Explore Variations**: Modify the algorithm for multiple sorted arrays, weighted medians, or streaming data.

* * *

Finding medians in sorted arrays is a fundamental problem with numerous applications. By mastering both brute force and optimized approaches, you’ll enhance your problem-solving skills and become proficient in efficient algorithm design.