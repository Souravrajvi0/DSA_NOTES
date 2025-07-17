---
difficulty: EASY
date_started: 
last_reviewed: 
Time Spent: 
---

TAGS CAN BE - - `#easy`, `#medium`, `#hard` `#revisit`, `#wrong`, `#must-do`, `#mistake
**TAGS**: #dsaproblem
**CONCEPT:** [[BFS-DFS IN MATRIX]]


## Problem Statement
Statement-Given a grid of size **n*m** (n is the number of rows and m is the number of columns in the grid) consisting of **'W'**s (Water) and **'L'**s (Land). Find the **number of islands**.  
  
**Note:** An island is either surrounded by water or the boundary of a grid and is formed by connecting adjacent lands **horizontally** or **vertically** or **diagonally** i.e., in all **8** directions.

**Examples:**

**Input:** grid[][] = [['L', 'L', 'W', 'W', 'W'], ['W', 'L', 'W', 'W', 'L'], ['L', 'W', 'W', 'L', 'L'], ['W', 'W', 'W', 'W', 'W'], ['L', 'W', 'L', 'L', 'W']]
**Output:** 4
**Explanation:**
The image below shows all the 4 islands in the grid.  
![](https://media.geeksforgeeks.org/img-practice/prod/addEditProblem/891756/Web/Other/blobid1_1743509451.jpg) 

**Input:** grid[][] = [['W', 'L', 'L', 'L', 'W', 'W', 'W'], ['W', 'W', 'L', 'L', 'W', 'L', 'W']]
**Output:** 2
**Expanation:**
The image below shows 2 islands in the grid.  
![](https://media.geeksforgeeks.org/img-practice/prod/addEditProblem/891756/Web/Other/blobid2_1743509488.jpg) 

**Constraints:**  
1 ≤ n, m ≤ 500  
grid[i][j] = {'L', 'W'}
link-https://www.geeksforgeeks.org/problems/find-the-number-of-islands/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card

@@
## Approach / Thought Process
## 🧠 Thought Process

1. **What was asked?**
   - [ ] Identify key input/output
   - [ ] What type of problem is it? DFS/BFS LAGEAG FOR SURE BUT YAHAN PE VISITED ARRAY KO USE KARKE LAGEGA

2. **What did I think at first?**

  JO 8 CHOICES HAIN UNKO IMPLEMENT KIS TRIKE SE KRTE HAIN!

3. **Other approaches I considered?**



4. **Why I chose this approach?**


   
### BRUTE FORCE: DFS LIKEHI HAI MAIN  YAHAN
TC:
```c++
  void dfs(int p , int q , vector<vector<char>>& grid,vector<vector<int>>&vis ){
      vis[p][q]=1;
      int n= vis.size();
      int m =vis[0].size();
      for(int i=-1;i<=1;i++){
          for(int j=-1 ;j<=1;j++){
              int x = p+i;
              int y=  q+j;
              if(x>=0&&y>=0&&x<n&&y<m&&grid[x][y]=='L'&&!vis[x][y]){  // VIS NA HO AND LAND HO AND OUT OF BOUND NA HO
                  dfs(x,y,grid,vis);
              }
          }
      }
  }
  
  
  
    int countIslands(vector<vector<char>>& grid) {
        // Code here
        int n = grid.size();
        int m = grid[0].size();
        vector<vector<int>>vis(n,vector<int>(m,0));// YE LINE KAFFI IMPORTANT HAI YAHI SE IDEA ATA HAI VIS ARRAY KO TRAVERSE KARKE DFS LAGANA HAI
        int islands=0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]=='L'&&!vis[i][j]){  // LAND HO AND VIS NA HO BAS
                    dfs(i,j,grid,vis);
                    islands++;
                }
            }
        }
        return islands;
    }
```

### OPTMISED VERSION  OR JUST BFS AUR LIKH SAKTE HAIN ISPE
TC:
```c++

```

### ANOTHER APPROACH IF NEEDED
TC:
```c++

```


3. **Chosen Solution**:
   - Describe the approach you settled on and why.
   - IF THERE IS ANY FURTHER OPTIMISATION

### MOST EFFICIENT APPROACH
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


## Similar Problems or Ideas about extended problems



## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.