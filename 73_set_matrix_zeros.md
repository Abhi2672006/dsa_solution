# Solution queue
```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int n=matrix.size();
        int m=matrix[0].size();
        queue<pair<int,int>> q;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(matrix[i][j]==0){
                    q.push({i,j});
                }
            }
        }int a,b;
        while(!q.empty()){
            a=q.front().first;
            b=q.front().second;
            q.pop();
            for(int i=0;i<n;i++){
                matrix[i][b]=0;
            }
             for(int i=0;i<m;i++){
             matrix[a][i]=0;
             }
             
        }
       
            }
};
```
## Complexity
**Time:**O(n*n)
**Space:**O(n)