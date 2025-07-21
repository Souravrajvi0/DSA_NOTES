---
difficulty: MEDIUM
date_started: 2025-07-20
last_reviewed: 2025-07-20
Time Spent: 60 minutes ++
---


TAGS CAN BE - - `#easy`, `#medium`, `#hard` `#revisit`, `#wrong`, `#must-do`, `#mistake
**TAGS**: #dsaproblem   #revisit 
**CONCEPT:** [[]]


## Problem Statement
Statement-You are given a weighted undirected graph having **n** vertices numbered from **1 to n** and **m** edges along with their weights. Find the **shortest** **weight** **path** between the vertex 1 and the vertex **n**,  if there exists a path, and return a list of integers whose first element is the **weight** of the path, and the rest consist of the nodes on that path. If no path exists, then return a list containing a single element **-1**.

The input list of edges is as follows - **{a, b, w}**, denoting there is an edge between **a** and **b**, and **w** is the weight of that edge.

**_Note:_** The driver code here will first check if the weight of the path returned is **equal** to the **sum** of the weights along the nodes on that path, if **equal** it will output the weight of the path, else **-2**. In case the list contains only a single element (**-1**) it will simply output **-1**. 

**Examples :**

**Input:** n = 5, m= 6, edges = [[1, 2, 2], [2, 5, 5], [2, 3, 4], [1, 4, 1], [4, 3, 3], [3, 5, 1]]
**Output:** 5
**Explanation:** Shortest path from 1 to n is by the path 1 4 3 5 whose weight is 5. 

**Input:** n = 2, m= 1, edges = [[1, 2, 2]]
**Output:** 2
**Explanation:** Shortest path from 1 to 2 is by the path 1 2 whose weight is 2. 

**Input:** n = 2, m= 0, edges = [ ]
**Output:** -1
**Explanation:** Since there are no edges, so no answer is possible.

**Expected Time Complexity:** O(m* log(n))  
**Expected Space Complexity:** O(n+m)

**Constraint:**  
2 <= n <= 106  
0 <= m <= 106  
1 <= a, b <= n  
1 <= w <= 105
link-https://www.geeksforgeeks.org/problems/shortest-path-in-weighted-undirected-graph/1

@@
## Approach / Thought Process
## 🧠 Thought Process

1. **What was asked?**
   - [ ] Identify key input/output
   - [ ] What type of problem is it?  DIJASTRA LAG RAHA HAI SAAF WO DIKHTA HAI!!!

1. **What did I think at first?**
Dijkastra lag raha hai saf ye dik raha hai! But mujhe problem ai ki main path kaise yad rkahon!!!
Dijkastra ek traversing algorithm bhi hai!
Just thoda sa memoisatio karke hum shortest path nikal sktte hain!

HINT - WHERE AM I COMING FROM?? YAD RAKHNA HAI!




3. **Other approaches I considered?**



4. **Why I chose this approach?**


   
### BRUTE FORCE:
TC:
```c++
class Solution {
  public:
    vector<int> shortestPath(int n, int m, vector<vector<int>>& edges) {
        // Code here
        vector<vector<pair<int,int>>> adj(n+1);
        for (auto& it : edges) {
            int u = it[0], v = it[1], w = it[2];
            adj[u].push_back({v, w});
             adj[v].push_back({u, w});
        }
        priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>>pq;
        vector<int>distance(n+1,INT_MAX);
        distance[1]=0;
        vector<int>parent(n+1);
        for(int i=1; i<=n; i++) parent[i] = i;
        pq.push({0,1});
        
        while(!pq.empty()){
            pair<int,int>temp = pq.top();
            pq.pop();
            
            int node = temp.second;
            
                for( auto it : adj[node]){
                    if(distance[node]+it.second<distance[it.first]){
                       distance[it.first] = distance[node]+it.second;
                       pq.push({distance[it.first],it.first});
                       parent[it.first] = node;
                    }
                }
            
            
        }
        
        vector<int>res;
        if(distance[n]==INT_MAX){
            res.push_back(-1);
            return res;
        }

        int i = n;
        while(i!=1){
            res.push_back(i);
            i = parent[i];
        }
        res.push_back(1);
        reverse(res.begin(),res.end());
        res.insert(res.begin(), distance[n]);
        return res;
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
| Complexity Type  | Value   |     |
| ---------------- | ------- | --- |
| Time Complexity  | **O()** |     |
| Space Complexity | **O()** |     |

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