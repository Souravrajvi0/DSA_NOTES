---
difficulty: MEDIUM
date_started: 2025-01-02
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [prefix sum](../DSA/DATA%20STRUCTURES%20&%20ALGORITHMS/Topics/PREFIX%20SUM/prefix%20sum.md)

PROBLEM LINK:https://leetcode.com/problems/count-vowel-strings-in-ranges/
## Problem Statement
> Copy the problem statement here for quick reference.
> You are given a **0-indexed** array of strings `words` and a 2D array of integers `queries`.

Each query `queries[i] = [li, ri]` asks us to find the number of strings present in the range `li` to `ri` (both **inclusive**) of `words` that start and end with a vowel.

Return _an array_ `ans` _of size_ `queries.length`_, where_ `ans[i]` _is the answer to the_ `i`th _query_.

**Note** that the vowel letters are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`
> 

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - LAGEGI TOH PREFIX SUM HI FOR SURE BUT AB PROBLEM YE AARHAHI HAI KI 
   - HOW CAN WE CHECK THAT THE INITIAL CHARACTER OF THE STRING IS A VOWEL OR NOT ???
   - OR KI JAGAH ASCII VALUES USE KARO// NAHI KAR SAKTA
   

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - MY BRUTE FORCE:
```c++
class Solution {
public:
  bool check(string s){ // TO CHECK A IF THE INITIAL CHARACTER AND THE LAST CHARACTER
  if(s[0]!='a'&&s[0]!='e'&&s[0]!='o'&&s[0]!='i'&&s[0]!='u'){
    return false;
  }
  if(s[s.size()-1]!='a'&&s[s.size()-1]!='e'&&s[s.size()-1]!='o'&&s[s.size()-1]!='i'&&s[s.size()-1]!='u'){
    return false;
  }
 return true;
  }
    vector<int> vowelStrings(vector<string>& words, vector<vector<int>>& queries) {
        
     vector<int>ans;
     vector<int>prefix(words.size(),0);

     if(check(words[0])){
        prefix[0]=1;
     }

     for(int i=1;i<words.size();i++){
     if(check(words[i])){
        prefix[i]=1+prefix[i-1];
      }
     else{
        prefix[i]=prefix[i-1];
         }
      }

    for(int i=0;i<queries.size();i++){
       int l=queries[i][0];
       int r=queries[i][1];

       if(l==0){
        ans.push_back(prefix[r]);
       }else{
        ans.push_back(prefix[r]-prefix[l-1]);
       }
    }
    return ans;
    }
};
```

KYA BEAUTUFUL USE HOGA YAHAN SET KA BHAI!!
INTUTION SAHI HAI BUT CODE BASS BETTER KARNA HAI!!!




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