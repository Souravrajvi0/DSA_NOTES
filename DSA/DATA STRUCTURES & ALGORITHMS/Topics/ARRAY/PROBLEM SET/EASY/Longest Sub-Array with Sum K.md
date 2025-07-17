---
difficulty: EASY
date_started: 2024-12-25
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [](.md)

PROBLEM LINK:
## Problem Statement
> Copy the problem statement here for quick reference.
> Given an array **`arr[]`** containing integers and an integer **`k`**, your task is to find the length of the longest subarray where the sum of its elements is equal to the given value `k`. It is guaranteed that a valid subarray exists.

**Examples:**

**Input:** arr[] = [10, 5, 2, 7, 1, 9], k = 15
**Output:** 4
**Explanation:** The subarray `[5, 2, 7, 1]` has a sum of 15 and length 4.

**Input:** arr[] = [-1, 2, -3], k = -2
**Output:** 3
**Explanation:** The subarray `[-1, 2, -3]` has a sum of -2 and length 3.

**Input:** arr[] = [1, -1, 5, -2, 3], k = 3
**Output:** 4
**Explanation:** The subarray `[1, -1, 5, -2]` has a sum of 3 and a length 4.

**Constraints:**  
1 ≤ arr.size() ≤ 106  
-109 ≤ arr[i], k ≤ 109

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - AGAR SARE POSITIVE TOH SLIDING WINDOW LAG JAEGI but negative bhi hai yahan toh thoda dhyan rakhna pad sakta hai

2. **Approach Options**:
   - Describe any alternative approaches you considered.
**BRUTE FORCE: GENERATING ALL SUBSEQUENCES** 
![Longest Sub-Array with Sum K-20241225212306808.webp](../../../../../../Images/Longest%20Sub-Array%20with%20Sum%20K-20241225212306808.webp)

![Longest Sub-Array with Sum K-20241225212347512.webp](../../../../../../Images/Longest%20Sub-Array%20with%20Sum%20K-20241225212347512.webp)

![Longest Sub-Array with Sum K-20241225212538943.webp](../../../../../../Images/Longest%20Sub-Array%20with%20Sum%20K-20241225212538943.webp)

![Longest Sub-Array with Sum K-20241225212555272.webp](../../../../../../Images/Longest%20Sub-Array%20with%20Sum%20K-20241225212555272.webp)

TC:O(N^3)











3. **Chosen Solution**:
   - Describe the approach you settled on and why.

## Code (C++)
```cpp
// C++ solution goes here
```

## Complexity Analysis
- **Time Complexity**: 
- **Space Complexity**: 

## Edge Cases
List any edge cases you considered, such as:
- Empty input
- Very large input
- Special cases (e.g., minimum/maximum values)

## Mistakes / Lessons Learned
Document any mistakes you made while solving, along with the solutions.
Write down any new techniques or patterns that you discovered while working on this problem.

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.