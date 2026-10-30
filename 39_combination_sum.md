# solution backtracking
```cpp
class Solution {
public: 
    vector<vector<int>> res;
    vector<int> ans;
    void find(int i,vector<int> & candidates,int target){
        if(target==0){
            res.push_back(ans);
            return ;
        }

        
        
        for(int j=i;j<candidates.size();j++){
            if(candidates[j]>target) break;;
            ans.push_back(candidates[j]);
            find(j,candidates,target-candidates[j]);
            ans.pop_back();
            
        }

    }
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        int n=candidates.size();
        sort(candidates.begin(),candidates.end());
            find(0,candidates,target);
        
        return res;
    }
};
```
## Complexity
**Time:**