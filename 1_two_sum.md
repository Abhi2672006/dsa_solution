# Two Sum

## Solution hash table

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> mp;
        
        int n=0;
        for(int i=0;i<nums.size();i++){
            n=target-nums[i];
            if(mp.find(n)!=mp.end() && i!=mp[n]) return {i,mp[n]};
             mp[nums[i]]=i;
        }
        return {};
    }
};
```
### Complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(n)