![[Images/image 37.png|image 37.png]]

![[Images/image 1 15.png|image 1 15.png]]

![[Images/image 2 13.png|image 2 13.png]]

![[Images/image 3 11.png|image 3 11.png]]

![[Images/image 4 10.png|image 4 10.png]]

![[Images/image 5 9.png|image 5 9.png]]

![[Images/image 6 9.png|image 6 9.png]]

![[Images/image 7 8.png|image 7 8.png]]

![[Images/image 8 8.png|image 8 8.png]]

![[Images/image 9 7.png|image 9 7.png]]

![[Images/image 10 6.png|image 10 6.png]]

![[Images/image 11 6.png|image 11 6.png]]

![[Images/image 12 6.png|image 12 6.png]]

![[Images/image 13 6.png|image 13 6.png]]

![[Images/image 14 6.png|image 14 6.png]]

![[Images/image 15 6.png|image 15 6.png]]

![[Images/image 16 5.png|image 16 5.png]]

![[Images/image 17 5.png|image 17 5.png]]

![[Images/image 18 5.png|image 18 5.png]]

![[Images/image 19 4.png|image 19 4.png]]

![[Images/image 20 4.png|image 20 4.png]]

![[Images/image 21 4.png|image 21 4.png]]

![[Images/image 22 4.png|image 22 4.png]]

[https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1](https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1)

vector<int> adj[] ⇒ ADJACENY LIST HAI YE

vector<vector<int>>& isConnected⇒ ADJACENCY MATRIX

## BFS

```C++


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
     if(!vis[it]){
        q.push(it);
        vis[it]=1;
           }
        }
     }
    return res;
    }
```

- **Time Complexity:** **O(V + E)**
- **Space Complexity:** **O(V + E)**

## DFS

![[Images/image 23 4.png|image 23 4.png]]

![[Images/image 24 4.png|image 24 4.png]]

![[Images/image 25 4.png|image 25 4.png]]

[https://www.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1](https://www.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1)

```C++
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

### Summary:

- **Time Complexity:** **O(V + E)**
- **Space Complexity:** **O(V + E)**