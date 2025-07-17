---
difficulty: EASY
date_started: 2024-12-25
last_reviewed: 
Time Spent: 
---
TAGS CAN BE - revise,important,easy
**TAGS**:
**CONCEPT:** [](.md)
IN NEXT REVISION DO THE INTERSECTION WALA QUESTION OF TWO ARRAY!
PROBLEM LINK:https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1
## Problem Statement
> Copy the problem statement here for quick reference.
> Given two **sorted** arrays **a[]** and **b[]**, where each array may contain **duplicate** elements , the task is to return the elements in the **union** of the two arrays in **sorted** order.

> Union of two arrays can be defined as the set containing distinct common elements that are present in either of the arrays.

**Examples:**

**Input**: a[] = [1, 2, 3, 4, 5], b[] = [1, 2, 3, 6, 7]  
**Output**: 1 2 3 4 5 6 7  
**Explanation**: Distinct elements including both the arrays are: 1 2 3 4 5 6 7.

**Input**: a[] = [2, 2, 3, 4, 5], b[] = [1, 1, 2, 3, 4]
**Output**: 1 2 3 4 5
**Explanation**: Distinct elements including both the arrays are: 1 2 3 4 5.

**Input**: a[] = [1, 1, 1, 1, 1], b[] = [2, 2, 2, 2, 2]
**Output**: 1 2
**Explanation**: Distinct elements including both the arrays are: 1 2.

**Constraints:**  
1  <=  a.size(), b.size()  <=  105  
-109  <=  a[i] , b[i]  <=  109


## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
BRUTE FORCE MEIN ORDERED SET KA USE KARNA KAFFI EASY RAHEGA!

**JAISE HI UNIQUE SUNO BHAI TOH SET/MAP MEIN DIMAG MEIN ANA CHAHIYE**

![Union of Two Sorted Arrays with Duplicate Elements-20241225181336150.webp](../../../../../../Images/Union%20of%20Two%20Sorted%20Arrays%20with%20Duplicate%20Elements-20241225181336150.webp)

![Union of Two Sorted Arrays with Duplicate Elements-20241225181413695.webp](../../../../../../Images/Union%20of%20Two%20Sorted%20Arrays%20with%20Duplicate%20Elements-20241225181413695.webp)

MY APPROACH


```c++
vector<int> findUnion(vector<int> &a, vector<int> &b) {
        // Your code here
        // return vector with correct order of elements
        vector<int>res;
        int n=a.size();
        int m=b.size();
        int i=0,j=0;
        while(i<n&&j<m){
            if(a[i]<b[j]){
                if(res.back()!=a[i])res.push_back(a[i]);
                i++;
            }else if(a[i]>b[j]){
                if(res.back()!=b[j])res.push_back(b[j]);
                
                j++;
            }else{
                if(res.back()!=a[i])res.push_back(a[i]);
                i++;
                j++;
                }
        }
    }
    AND THE REMANING PART
```

KUCH AESA SA AYA HAI FIRST THOUGHT FOR THIS PROBLEM

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - JO MERE APPRAOCH THI WOHI SAHI THI

3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - SET JADA TC THA ISLIYE

## Code (C++)
```cpp
// C++ solution goes here
  vector<int> findUnion(vector<int> &a, vector<int> &b) {
        // Your code here
        // return vector with correct order of elements
        vector<int>res;
        int n=a.size();
        int m=b.size();
        int i=0,j=0;
        while(i<n&&j<m){
            if(a[i]<=b[j]){
                if(res.size()==0||res.back()!=a[i])res.push_back(a[i]);
                i++;
            }else if(a[i]>b[j]){
                if(res.size()==0||res.back()!=b[j])res.push_back(b[j]);
                j++;
            }
        }
        while(j<m){
            if(res.size()==0||res.back()!=b[j])res.push_back(b[j]);
            j++;
        }
        
        while(i<n){
            if(res.size()==0||res.back()!=a[i])res.push_back(a[i]);
            i++;
        }
        return res;
    }
```

## Complexity Analysis
- **Time Complexity**: 
- **Space Complexity**: 
![Union of Two Sorted Arrays with Duplicate Elements-20241225182330884.webp](../../../../../../Images/Union%20of%20Two%20Sorted%20Arrays%20with%20Duplicate%20Elements-20241225182330884.webp)
## Edge Cases
List any edge cases you considered, such as:
- Empty input
- Very large input
- Special cases (e.g., minimum/maximum values)

## Mistakes / Lessons Learned
Document any mistakes you made while solving, along with the solutions.
Write down any new techniques or patterns that you discovered while working on this problem.
IN NEXT REVISION DO THE INTERSECTION WALA QUESTION OF TWO ARRAY!

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.