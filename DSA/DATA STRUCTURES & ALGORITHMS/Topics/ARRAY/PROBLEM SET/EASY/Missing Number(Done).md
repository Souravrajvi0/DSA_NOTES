---
difficulty: EASY
date_started: 2024-12-25
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [](.md)

PROBLEM LINK:https://leetcode.com/problems/missing-number/description/
## Problem Statement
> Copy the problem statement here for quick reference.
> Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return _the only number in the range that is missing from the array._

**Example 1:**

**Input:** nums = [3,0,1]
**Output:** 2
**Explanation:** n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.

**Example 2:**

**Input:** nums = [0,1]
**Output:** 2
**Explanation:** n = 2 since there are 2 numbers, so all numbers are in the range [0,2]. 2 is the missing number in the range since it does not appear in nums.

**Example 3:**

**Input:** nums = [9,6,4,2,3,5,7,0,1]
**Output:** 8
**Explanation:** n = 9 since there are 9 numbers, so all numbers are in the range [0,9]. 8 is the missing number in the range since it does not appear in nums.

**Constraints:**

- `n == nums.length`
- `1 <= n <= 104`
- `0 <= nums[i] <= n`
- All the numbers of `nums` are **unique**.

**Follow up:** Could you implement a solution using only `O(1)` extra space complexity and `O(n)` runtime complexity?

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - SORT AND FIND THE DIFFERENCE BETWEEN THE ADJACENT NUMBERS AND JAHAN 1 NAHI HUA
   - SORT AND COMPARE IT WITH INDEX VALUE
   - 

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - BRUTE FORCE:
   ![Missing Number-20241225184059778.webp](../../../../../../Images/Missing%20Number-20241225184059778.webp)

O(N^2)

HASHING APPROACH:
BHAI HASHING WITH A VISITED ARRAY CAN ALSO BE DONE!!!!


```c++
  int missingNumber(vector<int>& nums) {
        int n=nums.size();
        vector<int>vis(n+1,0);
        for(int i=0;i<n;i++){
            vis[nums[i]]=1;
        }
        int res;
        for(int i=0;i<n+1;i++){
            if(vis[i]==0){
                res=i;
                break;
            }
        }
       return res;
        
    }
```

TC:O(N)
SC:O(N)

THIS PROBLEM HAS TWO OPTIMAL SOLUTION!

**SUM OF N NATURAL NUMBERS:**

```c++
int missingNumber(vector<int>& nums) {
    int n=nums.size();
    int arrsum=0;
    for(int i=0;i<n;i++){
      arrsum+=nums[i];
    }
    int sum=n*(n+1)/2;
    return sum-arrsum;   
    }
```

TC: O(N)
SC:O(1)

**USING XOR**

![Missing Number-20241225191105028.webp](../../../../../../Images/Missing%20Number-20241225191105028.webp)

![Missing Number-20241225192447559.webp](../../../../../../Images/Missing%20Number-20241225192447559.webp)

![Missing Number-20241225192549085.webp](../../../../../../Images/Missing%20Number-20241225192549085.webp)

![Missing Number-20241225192702015.webp](../../../../../../Images/Missing%20Number-20241225192702015.webp)
NOW THIS IS O(N)
3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - XOR WITH ONE FOR LOOP!

## Code (C++)
```cpp
// C++ solution goes here
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
XOR
SUM
HASING WITH VIS ARRAY


## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.