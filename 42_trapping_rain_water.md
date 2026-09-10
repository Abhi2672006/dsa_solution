```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        int n=height.size();
        int left=0;
        int right=n-1;
        int l_max=0;
        int r_max=0;
        int block;
        
        while(left<=right){
            block=0;
             
            
            if(height[left]<height[right]){
                if(l_max<=height[left]){
                    l_max=max(l_max,height[left]);
                }
                else{
                     block=l_max-height[left];
                }
               
              
             
              left++;

            }
            else{
                 if(r_max<=height[right]){
                    r_max=max(r_max,height[right]);
                }
                else{
              
              
                 block=r_max-height[right];
                 
                }
                right--;

            }

            count+=block;
        }
        return count;

    }
};

```
## Complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(1)