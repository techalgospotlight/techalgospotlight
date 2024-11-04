---
title: "Insert Interval: A Comprehensive Guide to Solving LeetCode 57"
excerpt: "Learn how to solve the Insert Interval problem on LeetCode 57 using Python. This guide covers the problem statement, approach, and code solution to help you understand the problem and its solution."
date: Aug 24, 2024
layout: post
author: neha
categories:
    - data-structures-algorithms
image: assets/techalgospotlight-dsa-banner.webp
keywords: insert interval, insert interval leetcode, insert interval problem, insert interval python 
published: true
---

When working with intervals, a common problem is inserting a new interval into a set of existing, non-overlapping intervals while merging overlapping intervals. This is known as the **Insert Interval** problem, famously presented as **LeetCode 57**: **Insert Interval**.

In this article, we will explore the Insert Interval problem in depth, discussing its relevance, and applications, and providing a step-by-step guide to solving it efficiently. In this problem, you’ll improve your understanding of interval manipulation and be better equipped to tackle related problems in coding interviews.

* * *

Problem Statement
-----------------

The Insert Interval problem, as mentioned **57 Leetcode Problem**.

Given a set of non-overlapping intervals, insert a new interval into the intervals (merge if necessary). You may assume that the intervals were initially sorted according to their start times.

### Example 1:

**Input**: intervals = [[1,3],[6,9]], newInterval = [2,5]
**Output**: [[1,5],[6,9]]

### Example 2:

**Input**: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]  
**Output**: [[1,2],[3,10],[12,16]]

Your task is to write a function that takes in the **intervals** and **newInterval** as input and returns the updated list of intervals after inserting the **newInterval**.

Don’t forget about Constraints 😀

### Constraints:

*   0 <= intervals.length <= 104
*   intervals[i].length == 2
*   0 <= intervals[i][0] <= intervals[i][1] <= 104
*   intervals` is sorted by `intervals[i][0]
*   newInterval.length == 2
*   0 <= newInterval[0] <= newInterval[1] <= 104

* * *

Explanation
-----------

The problem requires **inserting a new interval** into a set of **existing, non-overlapping intervals** while **merging overlapping intervals**. The input intervals are sorted by their start times, and the output should also be sorted.

* * *

Insert Interval Example
-----------------------

```py
def insert(intervals, newInterval):
    result = []
    i = 0

    # Add intervals that come before the new interval
    while i < len(intervals) and intervals[i][1] < newInterval[0]:
        result.append(intervals[i])
        i += 1

    # Merge overlapping intervals
    while i < len(intervals) and intervals[i][0] <= newInterval[1]:
        newInterval[0] = min(newInterval[0], intervals[i][0])
        newInterval[1] = max(newInterval[1], intervals[i][1])
        i += 1

    # Add the new interval
    result.append(newInterval)

    # Add remaining intervals
    while i < len(intervals):
        result.append(intervals[i])
        i += 1

    return result
```


**This algorithm iterates through the intervals, merging overlapping intervals and inserting the new interval at the correct position.**

* * *

Example Walkthrough
-------------------

Let’s walk through an example to illustrate how the algorithm works:

### Input:

*   intervals = [[1,3],[6,9]]
*   newInterval = [2,5]

### Step-by-Step Walkthrough:

1.  Initialize an empty list result = []
2.  Iterate through **intervals** until we find the correct position to insert **newInterval**:
    *   i = 0, intervals[0] = [1,3], intervals[0][1] < newInterval[0], so add [1,3] to result
    *   i = 1, intervals[1] = [6,9], intervals[1][0] > newInterval[1], so break the loop
3.  Merge overlapping intervals:
    *   newInterval = [2,5], intervals[0] = [1,3], overlapping, so update newInterval = [1,5]
4.  Add the new interval:
    *   result = [[1,3], [1,5]], but we can merge these, so result = [[1,5]]
5.  Add remaining intervals:
    *   i = 1, intervals[1] = [6,9], add to result
6.  Return the updated list of intervals:
    *   result = [[1,5], [6,9]]

### Output:

*   **[[1,5], [6,9]]**

**So, this is how the algorithm merges overlapping intervals and inserts the new interval at the correct position.**

* * *

Variations and Edge Cases
-------------------------

Let’s see some variations and edge cases:

*   **Empty intervals list**: If the input **intervals** is an empty list, the function should return a list containing only the **newInterval**.
*   **No overlapping intervals**: If there are no overlapping intervals, the function should simply insert the **newInterval** at the correct position.
*   **Multiple overlapping intervals**: If there are multiple overlapping intervals, the function should merge all of them with the **newInterval**.
*   **New interval completely outside**: If the **newInterval** is completely outside the range of existing intervals, it should be added to the end or beginning of the list.
*   **New interval completely inside**: If the **newInterval** is completely inside an existing interval, it should be merged with that interval.
*   **Intervals with the same start or end value**: If two intervals have the same start or end value, they should be considered overlapping.

By handling these edge cases, we can ensure that our solution is robust and handles all possible scenarios.

* * *

Conclusion
----------

**Congratulations**! You’ve made it to the end of this comprehensive guide to solving the Insert Interval problem. You’ve learned:

1.  How to understand the problem and its constraints
2.  A step-by-step approach to solving the problem
3.  How to merge overlapping intervals
4.  How to handle edge cases and variations
5.  How to implement the solution in Python

By understanding this problem, you’ve improved your skills in:

*   Interval manipulation
*   Sorting and merging
*   Problem-solving and algorithm design

Remember, practice makes the coder perfect! Continue practising and solving similar problems to reinforce your understanding.

* * *

What’s Next?
------------

*   Try solving other interval-related problems, such as **Merge Intervals or Interval Partitioning**.
*   Explore other problem-solving strategies and techniques.
*   Practice coding and solving problems on platforms like **LeetCode, HackerRank, or CodeForces**.

**Keep learning and happy coding**! Don’t forget to Subscribe to **TechAlgoSpotlight**.