![image 37.png](../../../../../Images/image%2037.png)

![image 1 15.png](../../../../../Images/image%201%2015.png)

![image 2 13.png](../../../../../Images/image%202%2013.png)

![image 3 11.png](../../../../../Images/image%203%2011.png)

![image 4 10.png](../../../../../Images/image%204%2010.png)

![image 5 9.png](../../../../../Images/image%205%209.png)

![image 6 9.png](../../../../../Images/image%206%209.png)

![image 7 8.png](../../../../../Images/image%207%208.png)

![image 8 8.png](../../../../../Images/image%208%208.png)

![image 9 7.png](../../../../../Images/image%209%207.png)

![image 10 6.png](../../../../../Images/image%2010%206.png)

![image 11 6.png](../../../../../Images/image%2011%206.png)

![image 12 6.png](../../../../../Images/image%2012%206.png)

![image 13 6.png](../../../../../Images/image%2013%206.png)

when I'm writing here that ki  vector of arrays then it's fine
![GRAPH 1.1-20250711115508319.webp](../../../../../Images/GRAPH%201.1-20250711115508319.webp)
### 🟡 Summary

|Type|Declaration|Dynamic?|Best Use Case|
|---|---|---|---|
|Array of Vectors|`vector<int> g[N];`|❌|When `N` is known & small|
|Vector of Vectors|`vector<vector<int>> g(n);`|✅|When `n` is input-dependent|




![image 15 6.png](../../../../../Images/image%2015%206.png)

![image 16 5.png](../../../../../Images/image%2016%205.png)

![image 17 5.png](../../../../../Images/image%2017%205.png)

![image 18 5.png](../../../../../Images/image%2018%205.png)
THESE LEVELS ARE TRAVELLED TOGETHER!
![image 19 4.png](../../../../../Images/image%2019%204.png)

![image 20 4.png](../../../../../Images/image%2020%204.png)

![image 21 4.png](../../../../../Images/image%2021%204.png)

![image 22 4.png](../../../../../Images/image%2022%204.png)

[https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1](https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1)

BFS
```c++


vector<int> bfsOfGraph(int V, vector<int> adj[]) {
   int vis[n]={0};
    vis[0]=1;
    queue<int>q;
    q.push(0);
    vector<int>res;
    while(!q.empty()){
        int node =q.front();
        q.pop();
        res.push_back(node);
 
  for(auto it :adj[node]){  
     if(!vis[it]){          // WHILE LOOP K EK ITERATION MEIN EK NODE PROCESS HOTA HAI!!! AUR USKE SARE NEIGHBORS VISIT HOJATE                                 HAIN!
        q.push(it);
        vis[it]=1;
           }
        }
     }
    return res;
    }

```

Time Complexity: O(V+E)
Space Complexity: O(V+E)  ye kaise aya!?
Well har node ek bar process hoga queue mein (while loop) and uske bad uske neighbors process honge for k andar(Toh mtlb uski degres)
O(V+2E)
### **DFS**

![GRAPH 1.1-20250711121857655.webp](../../../../../Images/GRAPH%201.1-20250711121857655.webp)
![GRAPH 1.1-20250711122003073.webp](../../../../../Images/GRAPH%201.1-20250711122003073.webp)

![606](../../../../../Images/GRAPH%201.1-20250711122033160.webp)

https://www.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1


```c++
  void dfs(vector<int> adj[],vector<int>&vis,vector<int>&res,int node){
        vis[node]=1;
        res.push_back(node);
        
        for(auto it : adj[node]){
            if(!vis[it]){
                dfs(adj,vis,res,it);
            }
        }
    }
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
        // Code here
        vector<int>vis(V,0);
        vector<int>res;
        int start=0;
        dfs(adj,vis,res,start);
        return res;
    }
```

Time Complexity: O(V+E)
Space Complexity: O(V+E)
![GRAPH 1.1-20250714124457855.webp](../../../../../Images/GRAPH%201.1-20250714124457855.webp)
![GRAPH 1.1-20250714124543306.webp](../../../../../Images/GRAPH%201.1-20250714124543306.webp)
This is for undirected graph!

## What is a **Connected Component** in Graph Theory?

A **connected component** is like an **island of connected nodes** in a graph.

### ✅ Formally:

> A **connected component** in an **undirected graph** is a **subset of vertices** such that there is a **path between every pair of vertices** in this subset, and **no vertex in the subset** is connected to any **vertex outside** the subset.


## Why do we need **visited[] array**?

The `visited` array is **essential** in **DFS** or **BFS traversal** to:

### 1. ✅ **Avoid Revisiting Nodes**

Once you have visited a node and explored all nodes connected to it, you **mark it visited**. Without this, you'd keep going in **circles (infinite loops)**.

### 2. 🔍 **Track Progress**

It helps us **know which nodes have already been explored**, so we don’t reprocess them again.

### 3. 🧮 **Count Components**

Every time we find a **non-visited node**, it means we’ve discovered a **new connected component**.


