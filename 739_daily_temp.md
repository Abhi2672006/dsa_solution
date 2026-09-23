# Solution
**Topic:** Monotonic stack
```cpp
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& nums) {
        int n=nums.size();
        stack<int> a;
        if(n==1) return {0};
        vector<int> arr(n,0);
        
        for(int i=0;i<n;i++){
                while(!a.empty() && nums[i]>nums[a.top()]){
                    arr[a.top()]=i-a.top();
                    a.pop();
            }
            a.push(i);
        }
        return arr;

    }
};
```
## Complexity
- **Time:**O(n) 
- **Space:**O(n)