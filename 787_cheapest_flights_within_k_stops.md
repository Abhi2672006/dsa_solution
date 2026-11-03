# Solution
```cpp
class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int k) {
        vector<vector<pair<int,int>>> v(n);
        vector<int> dp(n,INT_MAX); // distance array
        dp[src]=0;
        queue<pair<int,pair<int,int>>> q;
        q.push({0,{src,0}}); //queue (steps,{src,cost}) initially 0 steps and cost=0 because reaching source costs nothing
        for(auto& it:flights){
            v[it[0]].push_back({it[1],it[2]});
        } // create an adjacency list
        int steps,s,c;
        while(!q.empty()){
                steps=q.front().first;
                s=q.front().second.first; //src
                c=q.front().second.second;// cost till now
                q.pop();
                if(steps>k) continue;
                int node,w;
                for(auto& x:v[s]){ //traverse the adjacency list
                    node=x.first; //0:{1,100} so node is 1 means path is 0->1 and cost is 100
                    w=x.second; //cost to reach
                    if(c+w<dp[node]){ //if cost + path weight < current weight to reaching that node then dp[node]=w+c
                        dp[node]=w+c;
                        q.push({steps+1,{node,w+c}});
                    }
                }
            }
        
        if(dp[dst]==INT_MAX) return -1;
        return dp[dst];
    }
};
```
