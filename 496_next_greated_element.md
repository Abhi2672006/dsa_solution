# Solution
**Topic:** Monotonic Stack

```cpp
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        int n1=nums1.size();
        int n2=nums2.size();
        stack<int> a;
        vector<int> arr(n1,-1);
        unordered_map<int,int> mp;
        for(int i=0;i<n2;i++){
            while(!a.empty() && nums2[i]>nums2[a.top()]){
                    mp[nums2[a.top()]]=nums2[i];
                    a.pop();
            }
            a.push(i);
        }
        
        for(int i=0;i<n1;i++){
            if(mp.find(nums1[i])!=mp.end()) arr[i]=mp[nums1[i]];
        }
        return arr;
    }
};
```
## Complexity
- **Time:**O(n2+n1)
- **Space:**O(n2)