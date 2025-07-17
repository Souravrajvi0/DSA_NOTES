---
difficulty: EASY
date_started: 2024-11-22
last_reviewed: 2024-11-22
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [Using set or map as a container which can only contain unique elements](../CONCEPTS/Using%20set%20or%20map%20as%20a%20container%20which%20can%20only%20contain%20unique%20elements.md)

PROBLEM LINK:https://leetcode.com/problems/unique-number-of-occurrences/description/
## Problem Statement
Given an array of integers `arr`, return `true` _if the number of occurrences of each value in the array is **unique** or_ `false` _otherwise_

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - SET AND MAP K USE KI FEEL ARAHI HAI!

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - MAP MEIN SABKI FREQUENCY LELO AND THEN SAVE KRTE JAO SET MEIN AND AND KOI FREQUENCY REPEAT HO VAHIN PANGA HAI!

3. **Chosen Solution**:
   - Describe the approach you settled on and why.

## Code (C++)
```cpp
// C++ solution goes here
//APPROACH 1
 bool uniqueOccurrences(vector<int>& arr) {
        unordered_map<int,int>mp;
        for(int i=0;i<arr.size();i++){
            mp[arr[i]]++;
        }
        unordered_set<int>s;
        for(auto it:mp){
           int oc=it.second;
           if(s.find(oc)!=s.end()){
            return false;
           }else{
            s.insert(oc);
           }
        }
        return true;
        
    }
//APPROACH 2
bool uniqueOccurrences(vector<int>& arr) {
        int i = 0;
        sort(arr.begin(),arr.end());
        vector<int> ans;
        while (i < arr.size()){
            int count = 1;
            for (int j = i+1; j< arr.size(); j++){
                if (arr[i] == arr[j])
                    count++;
            }
            ans.push_back(count);
            i = i + count;
        }
        sort(ans.begin(),ans.end());
        for (int i = 0; i < ans.size() - 1; i++){
            if (ans[i] == ans [i+1])
                return false;
        }
        return true;
    }
```

## Complexity Analysis
- **Time Complexity**: O(N)
- **Space Complexity**: O(N)

## Edge Cases
List any edge cases you considered, such as:
- Empty input
- Very large input
- Special cases (e.g., minimum/maximum values)

## Mistakes / Lessons Learned
Document any mistakes you made while solving, along with the solutions.
Write down any new techniques or patterns that you discovered while working on this problem.

It's a great problem in how we can use Set and map together!

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.