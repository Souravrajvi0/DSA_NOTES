---
share: true
---

## 🧠 Basic Concepts First

### 1. **What is a cycle?**

A **cycle** in an undirected graph means:

> You can start at a node, go through some edges, and come back to the same node **without repeating any edge or node (except the start node).**

### **Why BFS?**

- BFS (Breadth-First Search) explores nodes **level by level**.
    
- In an **undirected graph**, a cycle exists **if you encounter a node that has already been visited and is NOT the parent of the current node.**
### 🎯 Key idea:

> While doing BFS, if we visit an already visited node that is **not the parent** → **Cycle exists**.



## ✅ Algorithm

Let's break it down step-by-step.

### 🧩 Step 1: Prepare the Graph

We’ll use an **adjacency list** to represent the graph.
### 🧩 Step 2: Use a `visited` array to track which nodes we've seen.

### 🧩 Step 3: For every unvisited node, run BFS and check for cycle.

## The Intuition (in plain words)

### In an undirected graph:

Every edge is **bidirectional**, so when you go from `A → B`, you also have an edge `B → A`.

### So while traversing with BFS:

- If you reach a **node that you've already visited**, that could be a cycle.
    
- But wait! It might just be the node you **came from** (i.e., the **parent**).
    
- So the **real check** is:
    

> If a neighbor is already visited **and it is NOT the parent**, then you’ve found a **cycle**.

## During BFS

- Use a **queue** to do normal BFS.
    
- Instead of storing only the node in the queue, store a **pair: `(current_node, parent_node)`**
    
- Why? Because when we encounter a visited node, we need to check if it’s the parent — if it’s not, it means there's a back-edge (i.e., a cycle).

## Core Logic (Step-by-Step)

1. **Start BFS from any unvisited node.**
    
2. Use a queue to do the BFS traversal.
    
    - Each element in the queue is a **pair**: `{node, parent}`
        
3. For each neighbor of the current node:
    
    - If it's **not visited**, mark as visited and push `{neighbor, current}` to the queue.
        
    - If it's **already visited**:
        
        - And it's **not the parent**, then you've found a **cycle**.



![GRAPH 1.2-20250715144231452.webp](../../../../../Images/GRAPH%201.2-20250715144231452.webp)
## 🔁 Algorithm Setup

We’ll perform a BFS from an unvisited node, say `0`.  
We maintain:

- A **`visited[]` array**
    
- A **`queue<pair<node, parent>>`**
    

---

### 🔹 Initial State:

- `visited = [false, false, false, false, false, false]`
    
- `queue = empty`


![GRAPH 1.2-20250715144317687.webp](../../../../../Images/GRAPH%201.2-20250715144317687.webp)
![GRAPH 1.2-20250715144337850.webp](../../../../../Images/GRAPH%201.2-20250715144337850.webp)

![GRAPH 1.2-20250715144357173.webp](../../../../../Images/GRAPH%201.2-20250715144357173.webp)

## ✅ Final Result

As soon as we detect that:

- A neighbor is already visited
    
- And that neighbor is **not the parent**
    

👉 **We return true: Cycle exists.**

---

## 🧠 What just happened?

We were at `2`, and saw neighbor `4`:

- 4 was already visited from node `5`
    
- But we’re now seeing it again from node `2` (not parent)  
    ➡️ That means **two different paths** are trying to reach the same node → this creates a **loop**.


> In an **undirected graph**, if during traversal (BFS or DFS) you encounter a node that you've already visited **and** it's **not the parent**, then you're visiting that node through a **different path** → and **that forms a cycle**.

## ⚠️ Why do we need to check: “if neighbor is parent → ignore”?

Because in an **undirected graph**, every edge goes both ways.

![GRAPH 1.2-20250715144508760.webp](../../../../../Images/GRAPH%201.2-20250715144508760.webp)


![GRAPH 1.2-20250715144523155.webp](../../../../../Images/GRAPH%201.2-20250715144523155.webp)

## 🔁 Summary of Logic

| Condition                                 | Meaning                                   | Cycle? |
| ----------------------------------------- | ----------------------------------------- | ------ |
| `!visited[neighbor]`                      | First time visiting → proceed             | ❌ No   |
| `visited[neighbor] && neighbor == parent` | Just going back to the node you came from | ❌ No   |
| `visited[neighbor] && neighbor != parent` | Cycle exists                              | YES    |
```c++
class Solution {
  public:
  
   bool bfs(vector<int>&vis,int ini,vector<vector<int>>& edges){
   queue<pair<int,int>>q;
   q.push({ini,-1});
   vis[ini]=1;
   
   while(!q.empty()){
    pair<int,int>n=q.front();
    int node = n.first;
    int parent = n.second;
    q.pop();

     for( auto it : edges[node]){
        if(!vis[it]){
            vis[it]=1;
            q.push({it,node});
        }else if (it!=parent){
            return true;
        }
    }
   }
   return false;
  }  
  
    bool isCycle(int V, vector<vector<int>>& edges) {
        // Code here
       vector<vector<int>>adj(V);
       for(int i =0; i<edges.size(); i++){
        int u = edges[i][0];
        int v= edges[i][1];
        adj[u].push_back(v);
        adj[v].push_back(u);
    }
   vector<int>vis(V,0);
   
   for(int i = 0 ;i<V;i++){
    if(!vis[i]){
        if(bfs(vis,i,adj))return true;
    }
   }
    return false;
    }
};
```

Time Complexity: O(V+E)
Space Complexity: O()
![GRAPH 1.2-20250715144712044.webp](../../../../../Images/GRAPH%201.2-20250715144712044.webp)





## ✅ **Cycle Detection in Undirected Graph Using DFS**


## 💡 **1. Core Intuition**

In an **undirected graph**, a **cycle** exists if you revisit an already visited node **that is not the parent**.

This happens because:

- Every undirected edge is bidirectional.
    
- If you're at node `A` and go to `B`, you'll see `A` as a neighbor again from `B`.
    
- That’s **fine** because `A` is the **parent**.
    
- But if from `B` you go to a neighbor `C` that’s **already visited and not the parent**, then a **cycle exists**



## 🧠 **2. Core Logic**

We do a **DFS traversal**:

- Mark each node as visited
    
- For each neighbor:
    
    - If not visited → recursively DFS on it
        
    - If already visited **and it's not the parent**, it's a cycle
        

This is done for **all disconnected components**.



![GRAPH 1.2-20250717114905380.webp](../../../../../Images/GRAPH%201.2-20250717114905380.webp)

![GRAPH 1.2-20250717114947019.webp](../../../../../Images/GRAPH%201.2-20250717114947019.webp)





## 🚀 **5. Dry Run of DFS**

We start DFS from node `0`.

### Stack Trace:

- `dfs(0, -1)` → mark `0` as visited
    
    - neighbor `1` is unvisited → `dfs(1, 0)`
        
        - mark `1` visited
            
        - neighbor `2` is unvisited → `dfs(2, 1)`
            
            - mark `2` visited
                
            - neighbor `3` is unvisited → `dfs(3, 2)`
                
                - mark `3` visited
                    
                - neighbor `4` is unvisited → `dfs(4, 3)`
                    
                    - mark `4` visited
                        
                    - neighbor `0` is **already visited** and **not parent**  
                        → **Cycle detected! ✅**
                        

---

## 🎯 **6. Final Result**

DFS returns `true` → `isCycle()` returns `true`  
✅ **Cycle exists in the graph**


## 📌 **7. Logic Summary**

| Condition                             | Meaning                                      | Cycle?  |
| ------------------------------------- | -------------------------------------------- | ------- |
| `!vis[neighbor]`                      | First time → DFS deeper                      | ❌       |
| `vis[neighbor] && neighbor == parent` | Back edge to parent                          | ❌       |
| `vis[neighbor] && neighbor != parent` | Back edge to already visited node not parent | ✅ CYCLE |
![GRAPH 1.2-20250717115036211.webp](../../../../../Images/GRAPH%201.2-20250717115036211.webp)


```c++
class Solution {
public:
    bool dfs(int node, int parent, vector<vector<int>>& adj, vector<int>& vis) {
        vis[node] = 1;

        for (int neighbor : adj[node]) {
            if (!vis[neighbor]) {
                if (dfs(neighbor, node, adj, vis)) return true;
            } else if (neighbor != parent) {
                return true; // Cycle detected
            }
        }

        return false;
    }

    bool isCycle(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);

        // Build the graph
        for (auto& edge : edges) {
            int u = edge[0];
            int v = edge[1];
            adj[u].push_back(v);
            adj[v].push_back(u);
        }

        vector<int> vis(V, 0);

        for (int i = 0; i < V; i++) {
            if (!vis[i]) {
                if (dfs(i, -1, adj, vis)) return true;
            }
        }

        return false;
    }
};

```
## ✅ Works for:

- Connected graphs
    
- Disconnected graphs
    
- Self-loops
    
- Multi-component graphs
![GRAPH 1.2-20250717115238988.webp](../../../../../Images/GRAPH%201.2-20250717115238988.webp)

# ✅ **Cycle Detection in Directed Graph using BFS (Kahn's Algorithm)**

## 💡 1. **Intuition**

In a **directed acyclic graph (DAG)**, every node will eventually have in-degree 0 during **topological sort**.

> But if there is a **cycle**, then **some node's in-degree will never become 0** — meaning, you **cannot complete the topological order**.

So, if we try to perform **Kahn’s Algorithm** for topological sorting:

- If we can process **all `V` nodes** → ✅ No cycle
    
- If we get **stuck before visiting all nodes** → ❌ Cycle exists


## 🔁 2. **Core Logic**

- Build an adjacency list from edge list
    
- Track **in-degree** (incoming edges) of every node
    
- Initialize a queue with nodes having `in-degree = 0`
    
- While the queue is not empty:
    
    - Pop a node
        
    - For each of its neighbors:
        
        - Reduce their in-degree by 1
            
        - If their in-degree becomes 0 → push into queue
            
- Keep count of how many nodes you've processed
    
- **If processed nodes < V → cycle exists**


## ⚙️ 3. **Algorithm Setup**

### 📥 Input

- `V`: Number of nodes
    
- `edges`: Directed edges `u → v`
    

### 🛠️ Build Structures
```c++
vector<vector<int>> adj(V);
vector<int> indegree(V, 0);

for (auto [u, v] : edges) {
    adj[u].push_back(v);
    indegree[v]++;
}

```


![GRAPH 1.2-20250717142324835.webp](../../../../../Images/GRAPH%201.2-20250717142324835.webp)

## 🧪 5. **Dry Run on Example**

### Step 1: Queue initialization

Nodes with in-degree 0 → only `0`  
Queue = `[0]`

### Step 2: BFS loop

#### ⏳ Iteration 1:

- Pop `0`, process `1`
    
    - in[1] = 2 → 1 → still not 0
        
- Queue = `[]`
    
- Processed count = 1
    

Queue is now **empty**, but we have **not visited all nodes (only 1/4)**

→ 🔴 **Cycle detected**


## 🧠 7. Logic Summary

|Concept|Meaning|
|---|---|
|Topological sort completes|✅ No cycle|
|Topological sort stuck midway|❌ Cycle exists|
|In-degree never becomes zero|Part of a cycle|
|Kahn’s Algo → Node count < V|Cycle exists|

## ⏱️ 8. Time & Space Complexity

| Resource        | Complexity |
| --------------- | ---------- |
| Time            | `O(V + E)` |
| Space           | `O(V + E)` |
| In-degree array | `O(V)`     |
| Queue           | `O(V)`     |
| Adjacency list  | `O(V + E)` |
|                 |            |
|                 |            |

```c++
class Solution {
public:
    bool isCyclic(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        vector<int> indegree(V, 0);

        // Step 1: Build graph and in-degree array
        for (auto& edge : edges) {
            int u = edge[0];
            int v = edge[1];
            adj[u].push_back(v);
            indegree[v]++;
        }

        // Step 2: Initialize queue with in-degree 0 nodes
        queue<int> q;
        for (int i = 0; i < V; i++) {
            if (indegree[i] == 0)
                q.push(i);
        }

        int count = 0;

        // Step 3: BFS / Kahn's Algorithm
        while (!q.empty()) {
            int node = q.front();
            q.pop();
            count++;

            for (int neighbor : adj[node]) {
                indegree[neighbor]--;
                if (indegree[neighbor] == 0)
                    q.push(neighbor);
            }
        }

        // Step 4: If count < V → cycle exists
        return count != V;
    }
};

```

|Aspect|Value|
|---|---|
|Graph type|Directed|
|Algorithm used|Kahn’s (BFS)|
|Handles multiple components?|✅ Yes|
|Detects cycle?|✅ If count < V|
|Time Complexity|O(V + E)|
|Space Complexity|O(V + E)|

# ✅ Cycle Detection in Directed Graph using **DFS**
## 💡 1. **Intuition**

In a **directed graph**, a cycle exists if we **reach a node that is already on the current DFS path** (i.e., we revisit a node _before_ completing its entire recursion).

To detect that, we use:

- `vis[]`: to mark if a node has ever been visited
    
- `pathVis[]`: to mark if a node is currently part of the ongoing recursive DFS path
    

> If we find `vis[node] == 1` and `pathVis[node] == 1` during DFS — it means we're going in circles → **Cycle Detected**

---

## 🧠 2. Core Logic

- For every unvisited node:
    
    - Start DFS
        
    - Mark it visited in both `vis[]` and `pathVis[]`
        
    - For each neighbor:
        
        - If unvisited → DFS on it
            
        - If visited and on current path → cycle
            
    - After visiting all children, mark `pathVis[node] = 0` (backtrack)
        

---

## ⚙️ 3. Algorithm Setup

### 📥 Input

- `V`: Number of nodes
    
- `edges`: Directed edges `u → v`
    

### 🔧 Graph Building

```c++
vector<vector<int>> adj(V);
for (auto& edge : edges) {
    int u = edge[0], v = edge[1];
    adj[u].push_back(v);
}

```


![GRAPH 1.2-20250717142850009.webp](../../../../../Images/GRAPH%201.2-20250717142850009.webp)

![GRAPH 1.2-20250717142902511.webp](../../../../../Images/GRAPH%201.2-20250717142902511.webp)

## 📌 7. Logic Summary

|Condition|Interpretation|
|---|---|
|`!vis[nbr]`|Recurse normally|
|`vis[nbr] && pathVis[nbr]`|Cycle Detected ✅|
|After dfs, mark `pathVis[u]=0`|Remove from path 🔙|

---

## ⏱️ 8. Time & Space Complexity

|Aspect|Complexity|
|---|---|
|Time|O(V + E)|
|Space|O(V + E)|
|vis[], pathVis|O(V)|
|Recursion stack|O(V) max depth|
```c++
class Solution {
public:
    bool dfs(int node, vector<vector<int>>& adj, vector<int>& vis, vector<int>& pathVis) {
        vis[node] = 1;
        pathVis[node] = 1;

        for (int neighbor : adj[node]) {
            if (!vis[neighbor]) {
                if (dfs(neighbor, adj, vis, pathVis)) return true;
            } else if (pathVis[neighbor]) {
                return true; // Cycle detected
            }
        }

        pathVis[node] = 0; // backtrack
        return false;
    }

    bool isCyclic(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);
        for (auto& edge : edges) {
            int u = edge[0], v = edge[1];
            adj[u].push_back(v);
        }

        vector<int> vis(V, 0), pathVis(V, 0);

        for (int i = 0; i < V; i++) {
            if (!vis[i]) {
                if (dfs(i, adj, vis, pathVis)) return true;
            }
        }

        return false;
    }
};

```


## 🧠 10. Summary Table

|Approach|DFS (Directed)|
|---|---|
|Detects cycle?|✅ Yes|
|Handles components?|✅ Yes|
|Time Complexity|`O(V + E)`|
|Space Complexity|`O(V + E)`|
|Key trick|`pathVis[]` to track current path|
|Stops early?|✅ On first cycle|




# 🧠 What is Kahn's Algorithm?

Kahn's algorithm is a **BFS-based** way to perform **topological sorting** of a **DAG** (Directed Acyclic Graph).

### ✅ Key Idea:

> At every step, choose a node with **in-degree 0** (no incoming edges), process it, and remove it from the graph.

---

## 🔁 Why BFS Instead of DFS?

- DFS builds topological order using **postorder recursion**
    
- Kahn's algorithm builds it **layer-by-layer** using a queue
    
- It's more intuitive for “**task without prerequisites first**” kind of problems
    

---

## 📌 Definitions

- **In-degree** of a node = number of edges coming _into_ it
    
- A node with `in-degree 0` has **no prerequisites**
    

---

## ✅ Step-by-Step Algorithm

1. **Build the adjacency list** from the edges
    
2. **Compute in-degrees** of all nodes
    
3. **Push all nodes with in-degree 0** into a queue
    
4. While queue is not empty:
    
    - Pop a node, add it to the result
        
    - Reduce in-degree of its neighbors by 1
        
    - If any neighbor’s in-degree becomes 0, push it to the queue
        
5. If the result size ≠ number of nodes → there's a **cycle**


```c++
class Solution {
  public:
    void bfs(vector<int>& res, vector<vector<int>>& adj, vector<int>& indegree) {
        queue<int> q;
        
        for (int i = 0; i < indegree.size(); i++) {
            if (indegree[i] == 0) {
                q.push(i);
            }
        }

        while (!q.empty()) {
            int temp = q.front();
            q.pop();
            res.push_back(temp);
            for (auto it : adj[temp]) {
                indegree[it]--;           // jabh current task hogya mtlb a->b toh a hogya toh b ki indegree toh bhi kam hogi na 
                if (indegree[it] == 0) {  // indegree matlb outdegree hi hogi mtlb ki iske hone bad durse task ho skte hain na bhai!
                    q.push(it);           // indegree 0 mtlb isse pehle ab kisii ko nahi hona right toh ye ho jaega
                                          
                }
            }
        }
    }

    vector<int> topoSort(int V, vector<vector<int>>& edges) {
        vector<vector<int>> adj(V);


        for (auto it : edges) {
            adj[it[0]].push_back(it[1]); 
        }

        // ✅ Compute in-degrees
        vector<int> indegree(V, 0);
        for (int i = 0; i < V; i++) {
            for (auto it : adj[i]) {
                indegree[it]++;
            }
        }

        vector<int> res;
        bfs(res, adj, indegree);
        return res;
    }
};

```

| Complexity Type  | Value      |
| ---------------- | ---------- |
| Time Complexity  | **O(V+E)** |
| Space Complexity | **O(V+E)** |


## 🔑 Core Intuition of Kahn's Algorithm

Kahn’s Algorithm is based on a simple idea:

> **“If a task has no prerequisites, do it now.”**

That means:

- Find nodes with **in-degree 0** (no incoming edges)
    
- Process them → mark them as done
    
- Then reduce in-degrees of the nodes that depended on them
    
- If any of those now have `in-degree = 0`, add them to the queue
    
- Keep repeating

![GRAPH 1.3-20250716160002944.webp](../../../../../Images/GRAPH%201.3-20250716160002944.webp)

## Why It Works:

### 1. Nodes with in-degree 0 are **safe to process**:

- They have **no dependencies left**
    
- So they can go first in the topo sort
    

### 2. When you remove a node (A), all edges from it (A → B) are also removed:

- So reduce `in-degree` of B
    
- If B becomes 0 → it's ready next
    

### 3. This gives a **layer-by-layer BFS**:

- First all nodes with no prerequisites
    
- Then all nodes whose dependencies are completed
    
- And so on…


## 💥 What if there’s a cycle?

- Some nodes will **never reach in-degree 0**
    
- So queue will get stuck
    
- If `res.size() < V`, then 🔁 **cycle exists**
    

This is how Kahn's also **detects cycles** naturally.


> **"Why do we decrease the in-degree of adjacent nodes when we remove a node?"**

This is the _core intuition_ of Kahn’s Algorithm, so let me explain it with a super clear analogy and a simple breakdown.

![GRAPH 1.3-20250716160203021.webp](../../../../../Images/GRAPH%201.3-20250716160203021.webp)

### Step 1: Start with nodes with in-degree `0` → **A**

You process A.

That means:

> You’ve completed A, so **B no longer needs to wait for A.**

➡️ So you **decrease in-degree of B by 1**

Now B’s in-degree becomes `0`.

---

### 🔹 Step 2: Process B

Again, B is done.  
➡️ So C **no longer needs to wait for B** → decrease C’s in-degree by 1  
C becomes `0` → ready to process

### ✅ Intuition Rule

> **When you complete a task (node), remove its dependency effect on other tasks.**

That’s exactly what decreasing the in-degree does:

- The edge `A → B` means “B depends on A”
    
- Once A is done, you **eliminate that dependency**
    
- So B is **closer to being free to process**
    

---

## 🔨 Why Do We Need To Track In-Degree?

Because **in-degree tells us how many things a task is still waiting on.**

Only when in-degree becomes `0`, we can say:

> "This task is now free to run."

So reducing in-degree of adjacent nodes = removing a finished prerequisite from their waiting list.








# 🔁 **Cycle Detection in Graphs – Complete Comparison**

### 📊 Full Comparison Table

|Feature|🟢 **Undirected - DFS**|🟢 **Undirected - BFS**|🔵 **Directed - DFS**|🔵 **Directed - Kahn's Algo (BFS)**|
|---|---|---|---|---|
|**Technique**|DFS with parent tracking|BFS with `{node, parent}` pairs|DFS with `visited[]` + `pathVisited[]`|BFS with Topological Sort (in-degree)|
|**Cycle Condition**|Visited neighbor ≠ parent|Visited neighbor ≠ parent|If a node is visited again in the same DFS path|If topo sort doesn't include all `V` nodes|
|**Data Structures**|`visited[]`, recursive stack|`visited[]`, queue|`visited[]`, `pathVisited[]`|`inDegree[]`, queue|
|**Handles Disconnected?**|✅ Yes|✅ Yes|✅ Yes|✅ Yes|
|**Time Complexity**|`O(V + E)`|`O(V + E)`|`O(V + E)`|`O(V + E)`|
|**Space Complexity**|`O(V)`|`O(V)`|`O(V)`|`O(V)`|
|**Code Style**|Recursive|Iterative|Recursive|Iterative|
|**Use Case Preference**|Natural for DFS-heavy logic|Prefer BFS/queue style traversal|When recursion stack tracking is easy|When you're doing topological sort / checking DAG|

---

### ⚠️ Edge Cases to Consider

|Case|How to Handle|
|---|---|
|**Single Node, No Edges**|No cycle possible. Always return `false`.|
|**Disconnected Graph**|Always loop over all nodes (`for i in 0 to V`) to ensure full component check.|
|**Self-Loop (u → u)**|Always check `if neighbor == node` in both DFS and BFS. Return `true`.|
|**Parallel Edges (u ↔ v)**|Can cause false positives if you don't track parent in undirected graphs.|
|**Empty Graph (V=0)**|Return `false`. Edge list/adjacency list will be empty.|

---

### 🔀 When to Use What (Decision Tree)

> Use this quick guide to decide which method suits your use case best.

- **Undirected Graph**
    
    - 🧠 Use **DFS** if:
        
        - You’re comfortable with recursion.
            
        - Code needs to be compact.
            
    - 🔁 Use **BFS** if:
        
        - You prefer iterative logic or are BFS-focused.
            
- **Directed Graph**
    
    - 🧠 Use **DFS** if:
        
        - You want precise cycle detection based on call-stack path.
            
        - You're already doing DFS (like for coloring, path tracking).
            
    - 🧮 Use **Kahn’s Algorithm** if:
        
        - You’re checking if a graph is a DAG.
            
        - You're also generating a topological sort.
            

---

### ❗ Common Pitfalls (Gotchas)

| Mistake                                                    | Why It Fails                                         | Fix                                                          |
| ---------------------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| ❌ Not checking all nodes (disconnected)                    | Will miss components with cycles                     | Always loop over all nodes (`for i = 0 to V`)                |
| ❌ Not tracking parent in undirected graph                  | Can detect false cycles via bidirectional edges      | Track `parent` during DFS or push `{node, parent}` in BFS    |
| ❌ Not resetting pathVisited[] in DFS                       | Can mark nodes as cyclic incorrectly in directed DFS | `pathVis[node] = 0;` after DFS completes for the node        |
| ❌ Self-loop missed                                         | A node with edge to itself is always a cycle         | Check for `if neighbor == node` in both DFS and BFS          |
| ❌ In Kahn’s algo, assuming cycle if indegree=0 nodes exist | A few nodes with 0 indegree doesn’t imply no cycle   | Need to process all nodes and compare `count == V` for a DAG |