---
difficulty: MEDIUM
date_started: 2024-11-05
last_reviewed: 
time_spent: 
status: true
---
TAGS CAN BE - REVISE , IMPORTANT,
**TAGS**:
**CONCEPT:** [](.md)

PROBLEM LINK:https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1

## Problem Statement
Consider a rat placed at **(0, 0)** in a square matrix **mat** of order **n* n**. It has to reach the destination at **(n - 1, n - 1)**. Find all possible paths that the rat can take to reach from source to destination. The directions in which the rat can move are **'U'(up)**, **'D'(down)**, **'L' (left)**, **'R' (right)**. Value 0 at a cell in the matrix represents that it is blocked and rat cannot move to it while value 1 at a cell in the matrix represents that rat can be travel through it.  
**Note**: In a path, no cell can be visited more than one time. If the source cell is 0, the rat cannot move to any other cell. In case of no path, return an empty list. The driver will output **"-1"** automatically.
![RAT IN A MAZE-20241105133155452.webp](../../../../../Images/RAT%20IN%20A%20MAZE-20241105133155452.webp)



## Approach / Thought Process
1. **Initial Thoughts**: 
   - Write down your initial understanding and ideas for solving this problem.
   - Well mana ek grid hai toh jis bhi point par jaega atmax 4 possibilties rahegi for direction && BUT BLOCK 
   - EK FUNCTION CALL LAGEGEI AND FIRSE 4 possibilties aa jaegi
   - In case agar koi path nahi milta that meaning ki block agya we need to backtrack now backtrack aese karege ki jabh bhi visit kiya toh uss 0 ko 1 kardo and also ulte jate vaqt usko vapis 0 kardo
   

2. **Approach Options**:
   - Describe any alternative approaches you considered.
   - PEHLE WALA FUNCTION HUM DUSRE WALE KI BODY MEIN DAL SKTE HAIN LIKE SABSE PEHLE VOHI LIKH DO!!

3. **Chosen Solution**:
   - Describe the approach you settled on and why.

## Code (C++)
```cpp
// C++ solution goes here



bool canMove(int i, int j,vector<vector<int>> &mat){
      int n=mat[0].size();
      if(i<0||j<0||i==n||j==n||mat[i][j]==0||mat[i][j]==2){
          return false;
      }
      return true;
  }
  
  
  void mazeProblem(int i,int j,vector<vector<int>> &mat,string &s){
      
      
      if(i==mat[0].size()-1&&j==mat[0].size()-1){
        res.push_back(s);
        return;
      }
      
      mat[i][j]=2;
      // MOVE UP
      if(canMove(i-1,j,mat)){
          s+="U";
          mazeProblem(i-1,j,mat,s);
          s.pop_back();
      }
      // MOVE DOWN
      if(canMove(i+1,j,mat)){
          s+="D";
          mazeProblem(i+1,j,mat,s);
          s.pop_back();
       }
      // MOVE RIGHT
      if(canMove(i,j+1,mat)){
          s+="R";
          mazeProblem(i,j+1,mat,s);
          s.pop_back();

      }
      // MOVE LEFT
      if(canMove(i,j-1,mat)){
          s+="L";
          mazeProblem(i,j-1,mat,s);
          s.pop_back();

      }
      mat[i][j]=1;
      
    }
  
  
 
    vector<string> findPath(vector<vector<int>> &mat) {
        // Your code goes here
        // 0,0 se pass krte hain
        if(mat[0][0]==0){
            vector<string>e;
            return e;
        }
        string s="";
        mazeProblem(0,0,mat,s);
        return res;
        
    }
```

## Complexity Analysis
- **Time Complexity**: 
- **Space Complexity**: 

## Edge Cases
List any edge cases you considered, such as:

- If the starting point is blocked
- if we've already reached the ending 

## Mistakes / Lessons Learned
Document any mistakes you made while solving, along with the solutions.
Write down any new techniques or patterns that you discovered while working on this problem.
- Ye bat maine notice ki revert back to the before state/backtrack hum jabh kar rhae hain jabh ye reursion ki call end hone wale hai!! MTLB AB ISKE BAD CONTRIL JAEGA PURANE WALI CALL K ANDAR!!!!

## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: SANKET