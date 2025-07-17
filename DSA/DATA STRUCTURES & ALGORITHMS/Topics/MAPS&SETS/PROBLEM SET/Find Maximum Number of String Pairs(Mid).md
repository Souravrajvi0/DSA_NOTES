---
difficulty: EASY
date_started: 
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - REVISE , IMPORTANT,
**TAGS**: #revise 
**CONCEPT:** [Using set or map as a container which can only contain unique elements](../CONCEPTS/Using%20set%20or%20map%20as%20a%20container%20which%20can%20only%20contain%20unique%20elements.md)

PROBLEM LINK:https://leetcode.com/problems/find-maximum-number-of-string-pairs/description/
## Problem Statement
You are given a **0-indexed** array `words` consisting of **distinct** strings.

The string `words[i]` can be paired with the string `words[j]` if:

- The string `words[i]` is equal to the reversed string of `words[j]`.
- `0 <= i < j < words.length`.

Return _the **maximum** number of pairs that can be formed from the array_ `words`_._

Note that each string can belong in **at most one** pair.

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - EASY/DUMB APPROACH TOH YE HAI PEHLE SAB KO ADD KARLO AND THEN HAR STRING KO ULTA KARO AND THEN CHECK KI WO EXIST KRTA HAI YA NAHI IF DOESN'T EXIST THEN JUST MOVE ON KOI PAIR NAHI BANEGA ON THE OTHER HAND IF KOI PAIR BNTA HAI TOH JUST REMOVE THAT ELEMENT FROM THAT SET AND MOVE FORWARD TO THE NEXT!

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - EASY/DUMB
   - USING MAP

3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - USING MAP IS WAY BETTER

## Code (C++)
DUMB:
```cpp
// C++ solution goes here
class Solution {
public:
    int maximumNumberOfStringPairs(vector<string>& words) {
        unordered_set<string>s;
        int result=0;
        for(int i=0;i<words.size();i++){
            s.insert(words[i]);
        }
        for(int i=0;i<words.size();i++){
            string s1=words[i];
            reverse(s1.begin(),s1.end());
            if(s1==words[i])continue;
            if(s.find(s1)!=s.end()){
                result+=1;
                s.erase(words[i]);
            }
        }
        return result;     
    }
};
```

MERA CODE THODA REDUNDANT SA HAI!!!

USING MAP:
```c++
    int maximumNumberOfStringPairs(vector<string>& words) {
        int ans = 0;
        unordered_map<string, int> mp;
        for(auto w: words){
            string r = w;
            reverse(r.begin(), r.end());
            if(mp[r] > 0){ ans++; mp[r]--; }
            else mp[w]++;
        }
        return ans;
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

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.