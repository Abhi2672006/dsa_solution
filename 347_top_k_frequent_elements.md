# Solution one using unordered map and vector<int> storing frequency and number

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        unordered_map<int,int> mp;
        int n=nums.size();
        for(int i=0;i<n;i++){
            mp[nums[i]]++;
        }
        vector<pair<int,int>> vec(mp.begin(),mp.end());
        sort(vec.begin(),vec.end(),[](const auto &a,const auto &b){
            return a.second>b.second;
        });
        vector<int> a;
        for(int i=0;i<k;i++){
            a.push_back(vec[i].first);
        }
        return a;
    }
};
```
## Complexity
- **Time:**O(nlogn)
- **Space:**O(n)

# Solution two using bucket[freq] method avoid sorting

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        
        unordered_map<int,int> mp;
        int n=nums.size();
        for(int i=0;i<n;i++){
            mp[nums[i]]++;
        }
        vector<vector<int>> bucket(n+1);

        for(auto it:mp){
            bucket[it.second].push_back(it.first);
        }
       
        vector<int> arr;
        for(int i=n;i>=1;i--){
            for(auto it:bucket[i]){
                arr.push_back(it);
                if(arr.size()==k) return arr;
            }
        }
        return {};

    }
};
```

## complexity
- **Time:**O(n)
- **Space:**O(n) <!--we did not used sorting here-->