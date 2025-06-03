---
difficulty: HARD
status: true
date_started: 2024-11-04
last_reviewed: 2024-11-06
time_spent:
  - 60 mins
---
TAGS : #revise
CONCEPT: 
## Problem Statement
> The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return _all distinct solutions to the **n-queens puzzle**_. You may return the answer in **any order**.

Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.

## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - In a Way ek bat ye samajh aari hai ki check karni hai possibilties saari 
   - Aur in case koi tarika hai jismein kaam nahi bana toh ab backtrack bhi toh karna padega na !!!

2. **Approach Options**:
   - Describe any alternative approaches you considered.

3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - YAHAN PRUNNING YE HAI KI ROW=ROW+1
   - 

## Code (C++)
```cpp
// C++ solution goes here
class Solution {
public:
   vector<vector<char>>grid;

   bool canPlaceQueen(int row, int col,int n){
    for(int r=row-1;r>=0;r--){
        if(grid[r][col]=='Q'){
         return false;
        }
    }
   
    for(int r=row-1,c=col+1;r>=0&&c<n;r--,c++){
       if(grid[r][c]=='Q'){
        return false;
        }
    }

    for(int r=row-1,c=col-1;r>=0&&c>=0;r--,c--){
      if(grid[r][c]=='Q'){
        return false;
         }
       }
    return true;
   }

   void f(vector<vector<string>> &res,int row,int n){
     if(row==n){
        vector<string>l;
        for(int i=0;i<n;i++){
            string s="";
            for(int j=0;j<n;j++){
                s+=grid[i][j];
            }
            l.push_back(s);
        }
        res.push_back(l);
        
     }

       for(int col=0;col<n;col++){
          if(canPlaceQueen(row,col,n)){
               grid[row][col]='Q';
               f(res,row+1,n);  
               grid[row][col]='.';
           }
        }
    }


    vector<vector<string>> solveNQueens(int n) {
       grid.resize(n, vector<char>(n, '.'));
       vector<vector<string>> res;
       f(res,0,n);
       return res;
     }
};
```

## Complexity Analysis
- **Time Complexity**:The problem is often simplified to O(n!) due to the constraints that each queen must be placed in a unique row and column, which reduces the total number of configurations to consider. Further pruning by diagonal checks significantly reduces the search space. VARNA BINA CONSTRAINTS K O(n^n) Hoti!!
- **Space Complexity**: 
1. **Grid Storage:**
    - The grid is a n×nn \times nn×n matrix, so it takes O(n2)O(n^2)O(n2) space.
2. **Recursive Stack:**
    - The recursion depth is O(n)O(n)O(n), corresponding to one recursive call per row.
3. **Result Storage:**
    - Each valid solution requires storing nnn strings of length nnn, resulting in O(n2)O(n^2)O(n2) per solution.
    - If there are kkk solutions, the total space for storing solutions is O(k×n2)O(k \times n^2)O(k×n2).

### Summary

- **Time Complexity:** Roughly O(n!)O(n!)O(n!), but with significant pruning due to the backtracking and constraints.
- **Space Complexity:** O(n2+k×n2)O(n^2 + k \times n^2)O(n2+k×n2), where kkk is the number of solutions.

## Edge Cases
List any edge cases you considered, such as:
- Empty input ya 1* 1 ka matrix ko
- Very large input : Shayad Dikat de skta hai since TC jada hai
- Special cases (e.g., minimum/maximum values)

## Mistakes / Lessons Learned
Document any mistakes you made while solving, along with the solutions.
Write down any new techniques or patterns that you discovered while working on this problem.

YEHI TEMPLATE HAI BACKTRACKING KA!!!
PRUNING KA PART SOCHNE MEIN THODA DIMAG LAGTA HAI

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: SANKET BACKTRACKING