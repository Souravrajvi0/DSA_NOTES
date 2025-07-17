---
difficulty: EASY
date_started: 2024-12-23
last_reviewed: 2024-12-24
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**: #easy 
**CONCEPT:** [ARRAY SHIFTING](ARRAY%20SHIFTING.md)

PROBLEM LINK:https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/
## Problem Statement
> Given an array `nums`, return `true` _if the array was originally sorted in non-decreasing order, then rotated **some** number of positions (including zero)_. Otherwise, return `false`.

There may be **duplicates** in the original array.

**Note:** An array `A` rotated by `x` positions results in an array `B` of the same length such that `A[i] == B[(i+x) % A.length]`, where `%` is the modulo operation.
**Example 1:**

**Input:** nums = [3,4,5,1,2]
**Output:** true
**Explanation:** [1,2,3,4,5] is the original sorted array.
You can rotate the array by x = 3 positions to begin on the the element of value 3: [3,4,5,1,2].

**Example 2:**

**Input:** nums = [2,1,3,4]
**Output:** false
**Explanation:** There is no sorted array once rotated that can make nums.

**Example 3:**

**Input:** nums = [1,2,3]
**Output:** true
**Explanation:** [1,2,3] is the original sorted array.
You can rotate the array by x = 0 positions (i.e. no rotation) to make nums.
## Approach / Thought Process
1. **Initial Thoughts**: 
   - ![Check if Array Is Sorted and Rotated-20241223093655705.webp](../../../../../../Images/Check%20if%20Array%20Is%20Sorted%20and%20Rotated-20241223093655705.webp)
->If the array is sorted and rotated then only one deflection point will be seen such that! but this thought will be wrong because of the example 2 
->To check if a array is sorted two elements ko check karlo bass aur kya hi chahiye!
->Deflection points at max ek hi hoga in case of a sorted rotated array but also we need to consider the case of a circular rotation ki since rotate karenge tabh 
Even 0 deflection points bhi ho skte hain!

MY BAD CODE:

```c++

 bool check(vector<int>& nums) {
        int def=0;
        for(int i=0;i<nums.size()-1;i++){
            if(nums[i]>nums[i+1]){
             def++;
            }
        }
         if(def==0){
            return true;
        }else if(def==1&&nums[0]>=nums[nums.size()-1]){
         return true;
        }
        return false;
    }

```





1. **Approach Options**:
   - Describe any alternative approaches you considered.
   - VOHI HAI EK KI NUMBER OF DEFLECTION POINTS KITNE HAIN! AND ALSO DEFLECTIONS POINTS WALI CIRCULAR MEIN LAGNI CHAHIYE!

2. **Chosen Solution**:
   - Describe the approach you settled on and why.

## Code (C++)
```cpp
// C++ solution goes here


bool check(vector<int>& nums) {
        int n = nums.size();
        int count = 0;
        
        // Check if the array is non-decreasing
        for (int i = 1; i < n; i++)
            if (nums[i - 1] > nums[i])
                count++;
        
        // Check if the last element is greater than the first element
        if (nums[n - 1] > nums[0])
            count++;
        
        // If the count of violations is less than or equal to 1, return true
        return count < = 1;
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

YAHAN PAR NA CIRCULAR PROPERTY KA DHYAN RAKHNA 

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.