# solution greedy
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int farthest=0;
        int n=nums.size();
        for(int i=0;i<n;i++){
            if(i>farthest){
                return false;

            }
            else{
                farthest=max(farthest,i+nums[i]);
            }
        }
        return true;
    }
};

```
<!--In this farthest means at each point to which point we can reach at most means we are on first we check i> farthest? means can we reach till this point if not then false if yes then check to where farthest we can go from current point -->