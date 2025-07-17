---
difficulty: EASY
date_started: 2024-12-23
last_reviewed: 2024-12-24
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [](.md)

PROBLEM LINK:https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/
## Problem Statement
> Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each unique element appears only **once**. The **relative order** of the elements should be kept the **same**. Then return _the number of unique elements in_ `nums`.

Consider the number of unique elements of `nums` to be `k`, to get accepted, you need to do the following things:

- Change the array `nums` such that the first `k` elements of `nums` contain the unique elements in the order they were present in `nums` initially. The remaining elements of `nums` are not important as well as the size of `nums`.
- Return `k`.
**Input:** nums = [0,0,1,1,1,2,2,3,3,4]
**Output:** 5, nums = [0,1,2,3,4,_,_,_,_,_]
**Explanation:** Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
    - Using a set Data structure and iterating over the entire vector and then saving the elements inside the set and Such that everything in that set will be sorted and then saving everything in the vector
     Because set won't take repeated elements and since the vector is sorted then using an ordered set will save everything inside it in sorted order only!!
    - Since yahan par unique elements ki bat chl rahi hai toh it kinda makes sense to use 
1. **Approach Options**:
   - Describe any alternative approaches you considered.
   **BRUTE FORCE**:USING AN ORDERED SET
 ![Remove Duplicates from Sorted Array-20241223104833847.webp](../../../../../../Images/Remove%20Duplicates%20from%20Sorted%20Array-20241223104833847.webp)

**OPTIMISED SOLUTON: USING TWO POINTER** 
![Remove Duplicates from Sorted Array-20241224072421012.webp](../../../../../../Images/Remove%20Duplicates%20from%20Sorted%20Array-20241224072421012.webp)



2. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - TWO POINTER IS SURELY BETTER

## Code (C++)
```cpp
// C++ solution goes here
 int removeDuplicates(vector<int>& nums) {
        int L=0;
        for(int i=1;i<nums.size();i++){
            if(nums[i]!=nums[L]){
                nums[++L]=nums[i];
            }
        }
        return L+1;
    }
```

## Complexity Analysis
- **Time Complexity**: O(N)
- **Space Complexity**: O(1)

## Edge Cases
List any edge cases you considered, such as:
- Empty input 
- Very large input
- Special cases (e.g., minimum/maximum values)

## Mistakes / Lessons Learned
Document any mistakes you made while solving, along with the solutions.
Write down any new techniques or patterns that you discovered while working on this problem.

TWO POINTER KO AUR ACHE SE SOCH LIYA KAR ARRAY K QUESTIONS MEIN

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.