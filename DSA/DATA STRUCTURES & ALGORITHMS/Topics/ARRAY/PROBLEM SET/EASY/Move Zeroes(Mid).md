---
difficulty: EASY
date_started: 2024-12-25
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [](.md)

PROBLEM LINK:https://leetcode.com/problems/move-zeroes/description/
## Problem Statement
> Copy the problem statement here for quick reference.
> Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Note** that you must do this in-place without making a copy of the array.
**Example 1:**

**Input:** nums = [0,1,0,3,12]
**Output:** [1,3,12,0,0]

**Example 2:**

**Input:** nums = [0]
**Output:** [0]

**Constraints:**

- `1 <= nums.length <= 104`
- `-231 <= nums[i] <= 231 - 1`

**Follow up:** Could you minimize the total number of operations done?
#twopointer
## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - LAGEGA TOH TWO POINTER HI DIKH RAHA HAI SAF!
   - BHAI THODA DHYAN SE 

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - PEHLE MERA CODE DEKO!
MY BRUTE FORCE: O(N)
 
```c++
int n=nums.size();
        int i=0;
        for(;i<n;i++){
           if(nums[i]==0)break;
        }
        if(i==n-1||i==n)return;
        int j=i+1;
        for(;j<n;j++){
            if(nums[j]!=0){
              swap(nums[i],nums[j]);
              i++;
            }
        }
        
    }
```

SHIFTING/MOVING THE ELEMENTS IN THE ARRAY WITH THE HELP OF TWO POINTER
3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - BETTER OPTION GPT NE BATAYA 

## Code (C++)
```cpp
// C++ solution goes here
void moveZeroes(vector<int>& nums) {
    int i = 0;  // Pointer for the position of the next non-zero element
    
    for (int j = 0; j < nums.size(); j++) {
        if (nums[j] != 0) {
            swap(nums[i], nums[j]);
            i++;
        }
    }
}

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