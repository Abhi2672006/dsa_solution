# Solution backtracking 
```cpp
class Solution {
public:
    bool safe(int i,int j,const vector<pair<int,int>>& vis){
        
        for(const auto& x:vis){
            if(j==x.second) return false;
            if(abs(x.first-i)==abs(x.second-j)) return false;
        }
        return true;
    }
    void solve(int row, vector<pair<int,int>>& vis, int n,
           vector<vector<char>>& pq, vector<vector<string>>& ans) {
    if (row == n) {
        vector<string> board;
        for (auto& r : pq) board.push_back(string(r.begin(), r.end()));
        ans.push_back(board);
        return;
    }
        for(int j=0;j<n;j++){
                if(safe(row,j,vis)){
                    vis.push_back({row,j});
                    pq[row][j]='Q';
                    solve(row+1,vis,n,pq,ans);
                    pq[row][j]='.';
                    vis.pop_back();
                }
            }
    }
    vector<vector<string>> solveNQueens(int n) {
        vector<pair<int,int>> vis;
        vector<vector<char>> pq(n, vector<char>(n, '.'));
       
        vector<vector<string>> ans;
        solve(0,vis,n,pq,ans);
        return ans;
            
        

    }
};
```
<!-- This is very good question fro backtracking-->