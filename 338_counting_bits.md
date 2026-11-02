# Solution bit manipulation
```cpp
class Solution {
public:
    vector<int> countBits(int n) {
        vector<int> ans(n+1);
     
        int k;
        for(int i=0;i<=n;i++){
            int count=0;
            ans[i]=ans[i>>1]+(i&1);
            
            

        }
        return ans;
    }
};
```
## Complexity
**Time**O(n)
**Space:**O(1)