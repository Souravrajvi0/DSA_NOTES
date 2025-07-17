---
difficulty: EASY
date_started: 2024-11-22
last_reviewed: 2024-11-22
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**: #revise 
**CONCEPT:** [Using set or map as a container which can only contain unique elements](../CONCEPTS/Using%20set%20or%20map%20as%20a%20container%20which%20can%20only%20contain%20unique%20elements.md)

PROBLEM LINK:https://leetcode.com/problems/valid-anagram/description/
## Problem Statement
> Copy the problem statement here for quick reference.
> Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - First Approach Dimag mein ati hai using of Two maps and then comparing em

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - Using two Maps And Comparing em!
   - Using one map in a subtle way
   - Sort Both The strings and then just compare even that is so much better!

3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - One loop approach with

## Code (C++)
Chutiya Approach
```cpp
// C++ solution goes here
bool isAnagram(string s, string t) {
        if(s.length()!=t.length())return false;
        unordered_map<char,int>mp1;
        unordered_map<char,int>mp2;

        for(int i=0;i<s.length();i++){
         mp1[s[i]]++;
        }
        for(int i=0;i<t.length();i++){
         mp2[t[i]]++;
        }
       for(auto i:mp1){
        char c1=i.first;
        int f1= i.second;
        if(mp2.find(c1)!=mp2.end()){
            int f2=mp2[c1];
            if(f1!=f2)return false;
        }else{
            return false;
        }
       }
       return true;
    }
```

BETTER APPROACH:
```c++
bool isAnagram(string s, string t) {
        unordered_map<char, int> count;
        
        // Count the frequency of characters in string s
        for (auto x : s) {
            count[x]++;
        }
        
        // Decrement the frequency of characters in string t
        for (auto x : t) {
            count[x]--;
        }
        
        // Check if any character has non-zero frequency
        for (auto x : count) {
            if (x.second != 0) {
                return false;
            }
        }
        
        return true;
    }
```


```c++
if(s.size() != t.size()) return false;  
unordered_map<char, int>mpp;  
for(int i = 0; i < s.size(); i++) {  
mpp[s[i]]++;  
mpp[t[i]]--;  
}  
for(auto it : mpp) {  
if(it.second != 0) return false;  
}  
return true;
```

EK loop mein bhi kam ho jaega bhai!


Sorting the string:
```c++

bool isAnagram(string s, string t) {
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        return s == t;
    }
```





## Complexity Analysis
- **Time Complexity**: O(n)
- **Space Complexity**: O(n)

## Edge Cases
List any edge cases you considered, such as:
- Empty input
- Very large input
- Special cases (e.g., minimum/maximum values)

## Mistakes / Lessons Learned
Document any mistakes you made while solving, along with the solutions.
Write down any new techniques or patterns that you discovered while working on this problem.


Bhai Use map in a good way! Gadha Majdoori mat kiya kar!

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.