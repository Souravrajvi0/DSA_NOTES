---
difficulty: EASY
date_started: 2025-07-15
last_reviewed: 2025-07-15
Time Spent: 
---

TAGS CAN BE - - `#easy`, `#medium`, `#hard` `#revisit`, `#wrong`, `#must-do`, `#mistake
**TAGS**: #dsaproblem #easy 
**CONCEPT:** [[BFS-DFS IN MATRIX]]


## Problem Statement
Statement-You are given an image represented by an `m x n` grid of integers `image`, where `image[i][j]` represents the pixel value of the image. You are also given three integers `sr`, `sc`, and `color`. Your task is to perform a **flood fill** on the image starting from the pixel `image[sr][sc]`.

To perform a **flood fill**:

1. Begin with the starting pixel and change its color to `color`.
2. Perform the same process for each pixel that is **directly adjacent** (pixels that share a side with the original pixel, either horizontally or vertically) and shares the **same color** as the starting pixel.
3. Keep **repeating** this process by checking neighboring pixels of the _updated_ pixels and modifying their color if it matches the original color of the starting pixel.
4. The process **stops** when there are **no more** adjacent pixels of the original color to update.

Return the **modified** image after performing the flood fill.

**Example 1:**

**Input:** image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2

**Output:** [[2,2,2],[2,2,0],[2,0,1]]

**Explanation:**

![](https://assets.leetcode.com/uploads/2021/06/01/flood1-grid.jpg)

From the center of the image with position `(sr, sc) = (1, 1)` (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.

Note the bottom corner is **not** colored 2, because it is not horizontally or vertically connected to the starting pixel.

**Example 2:**

**Input:** image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, color = 0

**Output:** [[0,0,0],[0,0,0]]

**Explanation:**

The starting pixel is already colored with 0, which is the same as the target color. Therefore, no changes are made to the image.

**Constraints:**

- `m == image.length`
- `n == image[i].length`
- `1 <= m, n <= 50`
- `0 <= image[i][j], color < 216`
- `0 <= sr < m`
- `0 <= sc < n`
link-https://leetcode.com/problems/flood-fill/description/

@@
## Approach / Thought Process
## 🧠 Thought Process

1. **What was asked?**
   - [ ] Identify key input/output
   - [ ] What type of problem is it?

2. **What did I think at first?**
same feel thi as of bfs and dfs jada kuch fight thi nahi


3. **Other approaches I considered?**



4. **Why I chose this approach?**


   
### BRUTE FORCE:
TC:
```c++
class Solution {
public:
   void dfs(vector<vector<int>>& image, int sr, int sc, int color,int initialcolor){
    if(image[sr][sc]==color)return;
    image[sr][sc]=color;
    int n = image.size();
    int m = image[0].size();

    int dx [] = {-1,0,1,0};
    int dy [] = {0,1,0,-1};

    for(int i=0;i<4;i++){
        int x = sr+dx[i];
        int y = sc+dy[i];
        if(x>=0&&y>=0&&x<n&&y<m&&image[x][y]==initialcolor){
            dfs(image,x,y,color,initialcolor);
        }
    }
   }
   
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int n = image.size();
        int m = image[0].size();
        vector<vector<int>>vis(n,vector<int>(m,0));
        int intialcolor=image[sr][sc];
        dfs(image,sr,sc,color,intialcolor);
        return image;
    }
};
```

### OPTMISED VERSION 
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