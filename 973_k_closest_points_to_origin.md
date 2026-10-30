# Solution priority queue max heap

```cpp
class Solution {
public:
    vector<vector<int>> kClosest(vector<vector<int>>& points, int k) {
        priority_queue<pair<int,int>> pq;
        
        for(int i=0;i<(int)points.size();i++){
            pq.push({pow(points[i][0],2)+pow(points[i][1],2),i});
            if((int)pq.size()>k) pq.pop();
        }

        vector<vector<int>> res;
        while(!pq.empty()){
            res.push_back(points[pq.top().second]);
            pq.pop();
        }
        return res;
    }
};
```
**Time:**O(nlogn)