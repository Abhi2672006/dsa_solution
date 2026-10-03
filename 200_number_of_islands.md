# Solution dfs
```cpp
class Solution {
public:
  
    void dfs(vector<vector<char>>& grid,int i,int j){
         int n = grid.size(), m = grid[0].size();
        if (i < 0 || j < 0 || i >= n || j >= m || grid[i][j] != '1') return;

        grid[i][j] = '0';
        dfs(grid, i + 1, j);
        dfs(grid, i - 1, j);
        dfs(grid, i, j + 1);
        dfs(grid, i, j - 1);
    }
    int numIslands(vector<vector<char>>& grid) {
        int n=grid.size();
        int m=grid[0].size();
        int count=0;

        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]=='1'){
                     
                    count++;
                    dfs(grid,i,j);
                }
            }
        }
        return count;
    }
};
```
## Complexity
**Time:**O(n.m)
**Space:**O(n.m)

# Solution two bfs
```cpp
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        int n=grid.size();
        int m=grid[0].size();
        int dr[] = {1, -1, 0, 0};
        int dc[] = {0, 0, 1, -1};
        int ncol,nrow;
        int nr,nc;
        int count=0;
        queue<pair<int,int>> q;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]=='1'){
                    count++;
                    grid[i][j]='0';
                    q.push({i,j});
                    while(!q.empty()){
                        
                        nrow=q.front().first;
                        ncol=q.front().second;
                        q.pop();
                        for(int k=0;k<4;k++){
                            nr=nrow+dr[k];
                            nc=ncol+dc[k];
                          if (nr >= 0 && nr < n && nc >= 0 && nc < m && grid[nr][nc] == '1') {
                            grid[nr][nc] = '0';
                            q.push({nr, nc});
                        }
                }
                    }

                }
            }}
            return count;
        }
    
};
```
## complexity
**Time:**O(n.m)
**Space:**O(n.m)