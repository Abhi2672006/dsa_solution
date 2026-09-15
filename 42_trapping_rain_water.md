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
        int count=0;
        
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

# Solution two 
```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int n=height.size();
        int ml=0,mr=0;
        int left=0,right=n-1;

        while(left<=right){
            if(ml<=mr){
                if(ml<=height[left]) ml=height[left];
                else water+=ml-height[left];
                left++;
            }
            else{
                if(mr<=height[right]) mr=height[right];
                else water+=mr-height[right];
                right--;
            }

        }
        return water;
    }
};
```
## Complexity
- **Time:** O(n)
- **Space:**O(1)


