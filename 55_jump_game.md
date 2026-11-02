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

Like for example initially farthest=0 means wea re not started yet
these are stones 5 stone and each stone marked with number which shows how far we can go from stone like at stone 0 with 2 number we can go to 2 3 1 1 4 and stone 1 or stone 2 
stone 1:i=0 , nums[i]=2 here nums[i]+i>farthest so farthest  =2means from start we can go to 2 till now 
Stone 2:i=1 , nums[i]=3 here nums[i]+1>farthest so farthest =4 means from start we can go to 4 till now 
