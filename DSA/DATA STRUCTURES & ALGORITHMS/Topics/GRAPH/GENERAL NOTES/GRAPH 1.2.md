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



![[GRAPH 1.2-20250715144231452.webp]]
## 🔁 Algorithm Setup

We’ll perform a BFS from an unvisited node, say `0`.  
We maintain:

- A **`visited[]` array**
    
- A **`queue<pair<node, parent>>`**
    

---

### 🔹 Initial State:

- `visited = [false, false, false, false, false, false]`
    
- `queue = empty`


![[GRAPH 1.2-20250715144317687.webp]]
![[GRAPH 1.2-20250715144337850.webp]]

![[GRAPH 1.2-20250715144357173.webp]]

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

![[GRAPH 1.2-20250715144508760.webp]]


![[GRAPH 1.2-20250715144523155.webp]]

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
![[GRAPH 1.2-20250715144712044.webp]]





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



![[GRAPH 1.2-20250717114905380.webp]]

![[GRAPH 1.2-20250717114947019.webp]]





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
![[GRAPH 1.2-20250717115036211.webp]]


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
![[GRAPH 1.2-20250717115238988.webp]]

