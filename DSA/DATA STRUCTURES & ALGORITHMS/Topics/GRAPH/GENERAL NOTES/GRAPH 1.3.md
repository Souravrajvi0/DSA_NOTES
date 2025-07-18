### ✅ What is Topological Sort?

Topological sort is **a linear ordering of vertices in a Directed Acyclic Graph (DAG)** such that for every directed edge `u → v`, vertex `u` comes **before** `v` in the ordering.

### 1. What is a DAG?

**DAG** stands for **Directed Acyclic Graph**.

- **Directed**: Edges go in one direction. From `u → v`, not both.
    
- **Acyclic**: No cycles. You can't start at a node and come back to it by following the edges.
    

So basically:

- ✅ Directed graph
    
- ✅ No cycles
    
- ✅ Can be **topologically sorted** (i.e., nodes ordered such that all edges point forward in the list)


### 🔸 2. Why is DAG important?

DAGs are useful for:

- **Task Scheduling** (e.g., build systems like `Make`)
    
- **Course prerequisites**
    
- **Topological Sorting**
    
- **Version control**
    
- **Dependency graphs**


![GRAPH 1.3-20250716105131163.webp](../../../../../Images/GRAPH%201.3-20250716105131163.webp)

### 🔸 4. How to Represent a DAG in C++

We use an **adjacency list** for space-efficient representation.

Assuming we get edge list then we can can convert it into a adjacent list
```c++
  void addEdge(int u, int v) {
        adj[u].push_back(v); // Directed edge from u to v
    }
```

### 🔸5. Is My Graph a DAG?

To confirm a graph is a DAG:

- Use **DFS** to check if there’s a **cycle**.
    
- If **no cycle → it is a DAG**.

### 🔸 6. How to Detect Cycle in Directed Graph
DFS APPROACH

```c++
 bool dfs(vector<int>&vis,vector<int>&pathvis,vector<vector<int>>&adj,int i){
   vis[i]=1;
   pathvis[i]=1;
   for(auto it : adj[i]){
     if(!vis[it]){
        if(dfs(vis,pathvis,adj,it))return true;
     }else if(pathvis[it]){
        return true;
     }
   }
   pathvis[i]=0;
   return false;
   }

    bool isCyclic(int V, vector<vector<int>> &edges) {
        // code here
        vector<vector<int>>adj(V);
        for(auto it : edges){
            adj[it[0]].push_back(it[1]);
        }
        vector<int>vis(V,0);
        vector<int>pathvis(V,0);
        for(int i=0;i<V;i++){
            if(!vis[i]){
               if(dfs(vis,pathvis,adj,i)){
                return true;
               }
            }
        }
        return false;
    }
```

Time Complexity: O()
Space Complexity: O()


NOW COMING BACK TO TOPOLOGICAL SORT
**Why Topological Sort only works on Directed Acyclic Graphs (DAGs)**.??
![GRAPH 1.3-20250716105835950.webp](../../../../../Images/GRAPH%201.3-20250716105835950.webp)

![GRAPH 1.3-20250716105948470.webp](../../../../../Images/GRAPH%201.3-20250716105948470.webp)
### ✅ Why Do We Need Topological Sort?

We use it **whenever there's a dependency relationship**.

#### Real-world analogies:

- **Course Prerequisites**: You must take “Math 1” before “Math 2”. So, `Math 1 → Math 2`.
    
- **Task Scheduling**: Some tasks must be done before others (e.g., build dependencies).
    
- **Compilation Order**: Some files must be compiled before others.


### When Can We Do Topological Sort?

Only on a **Directed Acyclic Graph (DAG)**.

- **Directed**: Edges have direction.
    
- **Acyclic**: No cycles. Cycles make it impossible to determine what comes "first".

### ✅ Core Concept:

If `u → v`, then in the final list, `u` should appear **before** `v`.

🧠 How Topological Sort Works (Two Approaches)

### 1. **DFS-Based Topological Sort**:

In what order should we call DFS from the nodes? And does the starting point affect the final topological order??
 
 
 ## ✅ Does the **starting node** affect the final order?

### Short Answer:

**Yes**, it can affect the **exact topological order**,  
**but every valid order will still obey the topological constraint**:

> For every edge `u → v`, `u` comes before `v`.

So **there can be multiple valid topological sorts** depending on:

- The order in which we call DFS on unvisited nodes
    
- The adjacency list order

![GRAPH 1.3-20250716121118540.webp](../../../../../Images/GRAPH%201.3-20250716121118540.webp)


## ✅ Then How Do We Call DFS?

You loop through all nodes:


```c++
for (int i = 0; i < V; i++) {
    if (!vis[i]) {
        dfs(i, adj, vis, st);
    }
}
```

This ensures that:

- Even if the graph is **disconnected**, we process **every component**.
    
- And for every node, DFS ensures we process all its **dependencies first**.

### ✅ Key Point:

Topological sort is **not unique**.

### ✅ So What Should You Remember?

|Question|Answer|
|---|---|
|Does DFS start node affect result?|✅ Yes, it can give different valid topological orders|
|Are all of them correct?|✅ Yes, as long as all edges `u → v` have `u` before `v` in result|
|What if graph is disconnected?|🔁 Loop through all nodes from 0 to V-1 to cover all components|
|Should we reverse stack?|✅ Yes, because we push nodes **after** finishing their dependencies|

✅ Why Use a Stack in DFS Topological Sort?


## ✅ Why Use a Stack in DFS Topological Sort?

The **stack helps us reverse the order** in which nodes are finished in DFS.

### 🧠 Core Idea:

In topological sort, we want to **process a node _after_ all of its dependencies are handled**.

But in a normal DFS, we visit children first and return to parent later — so we don’t get the correct order **automatically**.

## Without Stack?

If you just print nodes when you visit them, you'll get **preorder**, not **postorder**.  
This would give incorrect topological sorting because dependencies may not be visited yet.

The **correct point** to record a node is **after all its children have been processed** — and that's what the stack captures.

![GRAPH 1.3-20250716123854919.webp](../../../../../Images/GRAPH%201.3-20250716123854919.webp)

![GRAPH 1.3-20250716123909633.webp](../../../../../Images/GRAPH%201.3-20250716123909633.webp)
## Step-by-step Dry Run

We go from node 0 to 5 in order.

---

### 🔹 i = 0

- `vis[0] == 0` → call `dfs(0)`
    
- `adj[0]` is empty → push `0`
    
- Stack: `[0]`
    

---

### 🔹 i = 1

- `vis[1] == 0` → call `dfs(1)`
    
- `adj[1]` is empty → push `1`
    
- Stack: `[0, 1]`
    

---

### 🔹 i = 2

- `vis[2] == 0` → call `dfs(2)`
    
- `adj[2] = {3}` → `vis[3] == 0` → call `dfs(3)`
    
    - `adj[3] = {1}` → `vis[1] == 1` → skip
        
    - push `3`
        
- Back to `dfs(2)` → push `2`
    
- Stack: `[0, 1, 3, 2]`
    

---

### 🔹 i = 3

- Already visited → skip
    

---

### 🔹 i = 4

- `vis[4] == 0` → call `dfs(4)`
    
- `adj[4] = {0, 1}` → both visited → push `4`
    
- Stack: `[0, 1, 3, 2, 4]`
    

---

### 🔹 i = 5

- `vis[5] == 0` → call `dfs(5)`
    
- `adj[5] = {0, 2}`
    
    - `0` is visited
        
    - `2` is visited
        
- push `5`
    
- Stack: `[0, 1, 3, 2, 4, 5]`


![GRAPH 1.3-20250716123951723.webp](../../../../../Images/GRAPH%201.3-20250716123951723.webp)
## 🔑 Final Answer:

> ❌ If you push the node _before_ visiting children, the stack's reversed result is **not guaranteed to be a valid topological order**.

Because:

- Topological sort is about **dependencies**
    
- You must ensure a node is added **only after its dependencies are fully processed**
    

That only happens when you **push the node _after_ its DFS call finishes**, i.e., **postorder**.

```c++
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    void dfs(int node, vector<int>& vis, vector<vector<int>>& adj, stack<int>& st) {
        vis[node] = 1;
        for (int nbr : adj[node]) {
            if (!vis[nbr]) {
                dfs(nbr, vis, adj, st);
            }
        }
        st.push(node); // ✅ Push after visiting all children
    }

    vector<int> topoSort(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        for (auto it : edges) {
            adj[it[0]].push_back(it[1]); // Directed edge: it[0] → it[1]
        }

        vector<int> vis(V, 0);
        stack<int> st;
        vector<int> res;

        for (int i = 0; i < V; i++) {
            if (!vis[i]) {
                dfs(i, vis, adj, st);
            }
        }

        while (!st.empty()) {
            res.push_back(st.top());
            st.pop();
        }

        return res;
    }
};

```

|Complexity Type|Value|
|---|---|
|Time Complexity|**O(V + E)**|
|Space Complexity|**O(V + E)**|


# ✅ Topological Sort in Directed Graph using **BFS (Kahn’s Algorithm)**

## 💡 1. **Intuition**

Topological sort is a **linear ordering of vertices** in a **Directed Acyclic Graph (DAG)** such that for every directed edge `u → v`, **`u` comes before `v`** in the ordering.

> In short: You must finish `u` before `v` if there's an edge from `u` to `v`.
> Think of it as a **dependency resolver** — where you must complete one task before starting another.
---

## 🧠 2. Core Logic (Kahn’s Algorithm)

The idea is to simulate the process of “scheduling tasks”:

- If a node has **no incoming edges (in-degree = 0)**, it can be processed first.
    
- Once a node is processed, reduce the in-degree of its neighbors (like finishing a task reduces dependencies).
    
- If a neighbor's in-degree becomes 0 → add it to queue.
    

Keep doing this until all nodes are processed.

We process nodes in the order of their **in-degree = 0**:

- These nodes have **no prerequisites** and can be safely added to the result
    
- Once a node is added, we **reduce the in-degree** of its neighbors (i.e., we’ve completed that task)
    
- If any neighbor’s in-degree becomes 0, it’s ready to be processed
    

Repeat until all nodes are processed.



## ⚙️ 3. Algorithm Setup



### 📥 Input

- `V`: Number of nodes (0 to V-1)
    
- `edges`: Directed edges `u → v`
    

### 🔧 Structures

- `adj[]`: adjacency list
    
- `indegree[]`: tracks incoming edges for each node
    
- `queue`: holds nodes with `indegree = 0`
    
- `result[]`: stores the final topological orde


![GRAPH 1.3-20250717211615160.webp](../../../../../Images/GRAPH%201.3-20250717211615160.webp)

![GRAPH 1.3-20250717211627554.webp](../../../../../Images/GRAPH%201.3-20250717211627554.webp)

## 🔁 5. Dry Run

### Initial Queue:

Nodes with `indegree = 0`: `4`, `5`  
Queue = `[4, 5]`

### Result = `[]`

### Process:

1. Pop `4` → Result: `[4]`
    
    - 0 (in--), 1 (in--)
        
    - in[0] = 1, in[1] = 1
        
2. Pop `5` → Result: `[4, 5]`
    
    - 0 (in--), 2 (in--)
        
    - in[0] = 0, in[2] = 0
        
    - Queue += `[0, 2]`
        
3. Pop `0` → Result: `[4, 5, 0]`
    
4. Pop `2` → Result: `[4, 5, 0, 2]`
    
    - 3 (in--) → in[3] = 0 → Queue += `[3]`
        
5. Pop `3` → Result: `[4, 5, 0, 2, 3]`
    
    - 1 (in--) → in[1] = 0 → Queue += `[1]`
        
6. Pop `1` → Result: `[4, 5, 0, 2, 3, 1]`


## 📌 7. Logic Summary

| Step               | Explanation                         |
| ------------------ | ----------------------------------- |
| In-degree 0        | Means no dependency → process it    |
| Decrease in-degree | Means one dependency is resolved    |
| Node enters queue  | When all its prerequisites are done |
| Cycle exists       | If final result has size < V        |

## ⏱️ 8. Time & Space Complexity

|Resource|Complexity|
|---|---|
|Time|O(V + E)|
|Space|O(V + E)|
|In-degree array|O(V)|
|Queue|O(V)|
|Adjacency list|O(V + E)|

```c++
class Solution {
public:
    vector<int> topoSort(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        vector<int> indegree(V, 0);

        // Build adjacency list and in-degree array
        for (auto& edge : edges) {
            int u = edge[0], v = edge[1];
            adj[u].push_back(v);
            indegree[v]++;
        }

        queue<int> q;
        for (int i = 0; i < V; i++) {
            if (indegree[i] == 0)
                q.push(i);
        }

        vector<int> result;

        while (!q.empty()) {
            int node = q.front();
            q.pop();
            result.push_back(node);

            for (int neighbor : adj[node]) {
                indegree[neighbor]--;
                if (indegree[neighbor] == 0)
                    q.push(neighbor);
            }
        }

        return result;
    }
};


```



## 🧠 7. Logic Summary

| Step              | Meaning                                 |
| ----------------- | --------------------------------------- |
| `indegree = 0`    | Node has no dependencies                |
| `q.push(i)`       | Node is ready to be scheduled           |
| `indegree[nbr]--` | Process dependency                      |
| `topo[]`          | Final sorted order (valid for DAG only) |