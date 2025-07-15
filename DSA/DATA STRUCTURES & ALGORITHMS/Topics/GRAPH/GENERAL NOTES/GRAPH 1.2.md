

## SUBPATTERN MATRIX MEIN BFS

MATRIX MEIN DATA KUCH REPRESENT KARTA HAI SO USKA TARVERSAL BHI DIFFERENT HOTA HAI

[https://www.geeksforgeeks.org/problems/find-the-number-of-islands/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card](https://www.geeksforgeeks.org/problems/find-the-number-of-islands/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)

```C++
  void bfs(vector<vector<char>>& grid,vector<vector<int>>&vis,int i,int j){
vis[i][j]=1;
int mr=grid.size();
int mc=grid[0].size();
queue<pair<int,int>>q;
pair<int,int>p;
p.first=i;
p.second=j;
q.push(p);
while(!q.empty()){
pair<int,int>L=q.front();
q.pop();
int s=L.first;
int r=L.second;
   for(int l=-1;l<=1;l++){
       for(int m=-1;m<=1;m++){
           if(l==0&&m==0)continue;
           int nx=s+l;
           int ny=r+m;
           if(nx<mr&&ny<mc&&nx>=0&&ny>=0&&grid[nx][ny]=='1'&&!vis[nx][ny]){
              vis[nx][ny]=1;
              pair<int,int>np;
              np.first=nx;
              np.second=ny;
              q.push(np);
           }
           }
       }
}
   }
int numIslands(vector<vector<char>>& grid) {
// Code here
int n=grid.size();
int m=grid[0].size();
vector<vector<int>>vis(n,vector<int>(m,0));
int count=0;
for(int i=0;i<n;i++){
for(int j=0;j<m;j++){
if(!vis[i][j]&&grid[i][j]=='1'){
count++;
bfs(grid,vis,i,j);
}
}
}
return count;
}
```

### [https://leetcode.com/problems/rotting-oranges/](https://leetcode.com/problems/rotting-oranges/)

→YAHAN PAR MINIMUM TIME MANGA HAI BHAI TOH DFS LAGANE KA KOI SENSE NAHI BNTA HAI

  

  

  

  

  

  

  

  

  

### [https://leetcode.com/problems/flood-fill/description/](https://leetcode.com/problems/flood-fill/description/)

```C++
vector<vector<int>> floodFill(vector<vector<int>>& i, int sr, int sc, int c) {
        int oc=i[sr][sc];
        if(i[sr][sc]==c)return i;
        int rows=i.size();
        int cols=i[0].size();
        vector<int>dx={-1,0,1,0};
        vector<int>dy={0,1,0,-1};
        queue<pair<int,int>>q;
        q.push({sr,sc});
        i[sr][sc]=c; 
         while(!q.empty()){
          pair<int,int>p=q.front();
          q.pop();
          int x=p.first;
          int y=p.second;
          for(int j=0;j<=3;j++){
            int nx=x+dx[j];
            int ny=y+dy[j];
              if(nx>=0&&ny>=0&&nx<rows&&ny<cols&&i[nx][ny]==oc){
                i[nx][ny]=c;
                q.push({nx,ny});
              }
        }
    } 
    return i;
    }
```

  

## Cycle in graph