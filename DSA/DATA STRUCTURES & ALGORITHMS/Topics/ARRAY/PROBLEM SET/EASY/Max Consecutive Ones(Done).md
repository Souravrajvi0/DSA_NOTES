---
difficulty: EASY
date_started: 2024-12-25
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [](.md)

PROBLEM LINK:https://leetcode.com/problems/max-consecutive-ones/description/
## Problem Statement
> Copy the problem statement here for quick reference.
> Given a binary array `nums`, return _the maximum number of consecutive_ `1`_'s in the array_.

**Example 1:**

**Input:** nums = [1,1,0,1,1,1]
**Output:** 3
**Explanation:** The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.

**Example 2:**

**Input:** nums = [1,0,1,1,0,1]
**Output:** 2

**Constraints:**

- `1 <= nums.length <= 105`
- `nums[i]` is either `0` or `1`.

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - ASAN THA YE DIRECT CHECK KAR LO

```c++
   int findMaxConsecutiveOnes(vector<int>& nums) {
        int max=0;
        int cn=0;
        int n=nums.size();
        for(int i =0;i<n;i++){
            if(nums[i]==1){
                cn++;
                if(cn>max){
                    max=cn;
                }
            }else{
                cn=0;
            }
        }
        return max;
    }
```


2. **Approach Options**:
   - Describe any alternative approaches you considered.

3. **Chosen Solution**:
   - Describe the approach you settled on and why.

## Code (C++)
```cpp
// C++ solution goes here
```

## Complexity Analysis
- **Time Complexity**: O(n)
- **Space Complexity**: O(1)

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