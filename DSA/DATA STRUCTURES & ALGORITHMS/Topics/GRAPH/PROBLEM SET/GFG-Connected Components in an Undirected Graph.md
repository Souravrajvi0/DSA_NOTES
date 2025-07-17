---
difficulty: EASY
date_started: 2025-07-14
last_reviewed: 2025-07-14
Time Spent: 10 minutes
---

TAGS CAN BE - - `#easy`, `#medium`, `#hard` `#revisit`, `#wrong`, `#must-do`, `#mistake
**TAGS**: #dsaproblem #easy
**CONCEPT:** [[BFS-DFS]]


## Problem Statement
Statement-Given an undirected graph with **V** vertices numbered from 0 to V-1 and **E** edges, represented as a 2D array **edges[][]**, where each entry **edges[i] = [u, v]** denotes an edge between vertices **u** and **v**.

Your task is to return a list of all connected components. Each connected component should be represented as a list of its vertices, with all components returned in a collection where each component is listed separately.

**Note:** You can return the components in any order, driver code will print the components in **sorted** order.

**Examples :**

**Input:** V = 5, edges[][] = [[0, 1], [2, 1], [3, 4]]
**Output:** [[0, 1, 2], [3, 4]]
**Explanation:  
![](https://media.geeksforgeeks.org/img-practice/prod/addEditProblem/893290/Web/Other/blobid1_1744798106.jpg)**

**Input:** V = 7, edges[][] **=** [[0, 1], [6, 0], [2, 4], [2, 3], [3, 4]]
**Output:** [[0, 1, 6], [2, 3, 4], [5]]  
**Explanation:  
![](https://media.geeksforgeeks.org/img-practice/prod/addEditProblem/893290/Web/Other/blobid0_1744797809.jpg)**

**Constraints:  
**1 ≤ V ≤ 105  
1 ≤ edges.size() ≤ 105  
0 <= edges[i][0], edges[i][1] < V
link-https://www.geeksforgeeks.org/problems/connected-components-in-an-undirected-graph/1

@@
## Approach / Thought Process
## 🧠 Thought Process

1. **What was asked?**
   - [ ] Identify key input/output
   - [ ] What type of problem is it? BFS AND DFS BAS PATH YAD RAKHNA HAI!!!

1. **What did I think at first?** 
    Converting the edge matrix into the adj list that was something to learn!


2. **Other approaches I considered?**



3. **Why I chose this approach?**


   
### BRUTE FORCE:
TC:
```c++
vector<int>bfs(vector<int>&vis,vector<vector<int>>&adj,int cur){
         vector<int>res;
         queue<int>q;
         q.push(cur);
         vis[cur]=1;
         while(!q.empty()){
             int node = q.front();
             q.pop();
             res.push_back(node);
             for(auto it : adj[node]){
                 if(!vis[it]){
                     vis[it]=1;
                     q.push(it);
                 }
                 
             }
         }
         return res;
         
     }
  
    vector<vector<int>> getComponents(int V, vector<vector<int>>& edges) {
        // code here
        vector<vector<int>>adj(V);
        for(int i=0 ; i<edges.size();i++){
            int u= edges[i][0];
            int v= edges[i][1];
            adj[u].push_back(v);
            adj[v].push_back(u);
        }
        vector<vector<int>>res;
        vector<int>vis(V,0);
        for(int i=0 ;i<V;i++){
            if(!vis[i]){
               res.push_back(bfs(vis,adj,i));
            }
        }
        return res;
    }
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

## **Adjacency Matrix → Adjacency List**

### 🔷 Matrix Input:

```c++
adj = {
    {1, 2},    // node 0 connected to 1, 2
    {0, 2},    // node 1 connected to 0, 2
    {1, 0}     // node 2 connected to 1, 0
}
```

```c++
int V = isConnected.size();
vector<vector<int>> adj(V);

for (int i = 0; i < V; i++) {
    for (int j = 0; j < V; j++) {
        if (isConnected[i][j] == 1 && i != j) {
            adj[i].push_back(j);
            // Don't push adj[j].push_back(i) again — it's already symmetric in undirected graphs
        }
    }
}
```


## Additional Resources
- **Discussion Links**: Links to relevant discussions or solutions that provide additional insights.
- **Reference Links**: Any articles, videos, or other resources that helped you understand the problem better.