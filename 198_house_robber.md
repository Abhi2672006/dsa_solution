# solution space optimization dp
```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        int prev1=0;
        int prev2=0;
        int newc;
        for(int n:nums){
            newc=max(prev1,prev2+n);
            prev2=prev1;
            prev1=newc;
        }
        return prev1;
    }

};
```

## complexity
**Time:** O(n)
**Space:**O(1)