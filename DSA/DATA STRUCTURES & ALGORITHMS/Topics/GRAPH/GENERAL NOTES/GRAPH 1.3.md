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


![[GRAPH 1.3-20250716105131163.webp]]

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
![[GRAPH 1.3-20250716105835950.webp]]

![[GRAPH 1.3-20250716105948470.webp]]
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

![[GRAPH 1.3-20250716121118540.webp]]


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

![[GRAPH 1.3-20250716123854919.webp]]

![[GRAPH 1.3-20250716123909633.webp]]
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


![[GRAPH 1.3-20250716123951723.webp]]
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

![[GRAPH 1.3-20250716160002944.webp]]

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

![[GRAPH 1.3-20250716160203021.webp]]

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