---
difficulty: EASY
date_started: 2024-11-22
last_reviewed: 2024-11-22
Time Spent: 30Minutes
---
TAGS CAN BE - REVISE , IMPORTANT,EASY
**TAGS**: #EASY 
**CONCEPT:** [Using set or map as a container which can only contain unique elements](../CONCEPTS/Using%20set%20or%20map%20as%20a%20container%20which%20can%20only%20contain%20unique%20elements.md)

PROBLEM LINK:https://leetcode.com/problems/count-number-of-distinct-integers-after-reverse-operations/description/
## Problem Statement

You are given an array `nums` consisting of **positive** integers.

You have to take each integer in the array, **reverse its digits**, and add it to the end of the array. You should apply this operation to the original integers in `nums`.

Return _the number of **distinct** integers in the final array_


## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - Since I can feel we're only asked the number of distinct numbers in the set and agar mujhse actual digits puch liye jate instead of asking me the real order tabh tak set data structure mein koi dikkat nahi hoti! 

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - Set lagane ki feel ari hai!

3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - First Approach using SET

## Code (C++)
```cpp
// C++ solution goes here
class Solution {
public:
    int rev(int num){
     int reversed = 0;
        while (num) {
            int last = num % 10;
            reversed = reversed * 10 + last;
            num /= 10;
        }
        return reversed;
    }
   // TO REVERSE A  NUMBER THE ABOVE TEMPLATE IS PRETTY GOOD!
    
    
    int countDistinctIntegers(vector<int>& nums) {
        unordered_set<int>s;
          for(int i=0;i<nums.size();i++){
            int revn=rev(nums[i]);
            s.insert(revn);
            s.insert(nums[i]);
        }
        return s.size();
    }
};
```

## Complexity Analysis
Approach 1:
- **Time Complexity**: O(n)
- **Space Complexity**: O(n)


Approach 2nd:
![Count Number of Distinct Integers After Reverse Operations(Done)-20241122082723092.webp](../../../../../Images/Count%20Number%20of%20Distinct%20Integers%20After%20Reverse%20Operations(Done)-20241122082723092.webp)
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