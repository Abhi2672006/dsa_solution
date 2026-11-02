# solution
```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        sort(intervals.begin(),intervals.end());
        vector<vector<int>> ans;
        vector<int> v;
        int y;
        ans.push_back(intervals[0]);
        if(intervals.size()==1) return intervals;
        for(int i=1;i<intervals.size();i++){
           if(ans.back()[1]>=intervals[i][0]){
            ans.back()[1]=max(ans.back()[1],intervals[i][1]);
           }else{
            ans.push_back(intervals[i]);
           }
        }
        return ans;
    }
};
```
## Complexity
**Time:**O(n)
**Space:**O(n);