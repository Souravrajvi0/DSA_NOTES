---
difficulty: EASY
date_started: 2024-12-24
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [](.md)

PROBLEM LINK:
## Problem Statement
> Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

**Example 1:**

**Input:** nums = [1,2,3,4,5,6,7], k = 3
**Output:** [5,6,7,1,2,3,4]
**Explanation:**
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]

**Example 2:**

**Input:** nums = [-1,-100,3,99], k = 2
**Output:** [3,99,-1,-100]
**Explanation:** 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]

**Follow up:**

- Try to come up with as many solutions as you can. There are at least **three** different ways to solve this problem.
- Could you do it in-place with `O(1)` extra space?
## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - k=k%n; kinda makes sure we always need to rotate such like ki wo rotation less than size hi hoga 
   - Then Using an extra array and some jugad will be the brute force approach for sure!

2. **Approach Options**:
   - Describe any alternative approaches you considered.
BRUTE FORCE
```c++
 void rotate(vector<int>& nums, int k) {

        int n=nums.size();
        k%=n;

        vector<int>res(n);
        int i;
        for( i=0;i+k<n;i++){
          res[i+k]=nums[i];
        }
        for(int j=0;i<n;i++,j++){
            res[j]=nums[i];
        }
        nums=res;
    }
```

TC: O(2N)
SC:O(N)


OPTIMAL SOLUTION:


```c++
void rev(vector<int>&nums,int low,int high){
   while(low<=high){
    swap(nums[low],nums[high]);
    low++;
    high--;  
    }
    }
    void rotate(vector<int>& nums, int k) {
    int n=nums.size();
    k%=n;
    rev(nums,0,n-1);  
    rev(nums,0,k-1);
    rev(nums,k,n-1);
    }
```







3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - SECOND WALA!!
   - ISKA SOLUTION SAMJHANA PADEGA ACHE SE 

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