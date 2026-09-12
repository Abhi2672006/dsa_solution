# Solution one using two arrays - prefix sum
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n=nums.size();
        vector<int> pre(n,0);
        vector<int> suff(n,0);

        pre[0]=1;
        suff[n-1]=1;
        int product=1;
        for(int i=1;i<n;i++){
            pre[i]=nums[i-1]*product;
            product=nums[i-1]*product;
            cout<<pre[i];
        }
        product=1;
        for(int i=n-2;i>=0;i--){
           suff[i]=nums[i+1]*product;
           product=nums[i+1]*product;
           cout<<suff[i];
        }
        for(int i=0;i<n;i++){
            suff[i]=suff[i]*pre[i];
        }

        
return suff;
    }
};
```
## Complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(n^2)

# Solution two space complexity O(n)
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n=nums.size();
      
        vector<int> suff(n,0);

        int pre=1;
        suff[n-1]=1;
        int product=1;
      
       
        for(int i=n-2;i>=0;i--){
           suff[i]=nums[i+1]*product;
           product=nums[i+1]*product;
          
        }
        
        product=1;
          for(int i=1;i<n;i++){
            pre=nums[i-1]*product;
            product=nums[i-1]*product;
            suff[i]*=pre;
            
        }
return suff;
    }
};
```
## Complexity 
- **Time Complexity:**O(n)
- **Space Complexity:**O(1)

# Solution three same but cleaner approach
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        vector<int> ans(n, 1);

        int pre = 1;

        for(int i = 0; i < n; i++){
            ans[i] = pre;
            pre *= nums[i];
        }

        int suffix = 1;

        for(int i = n - 1; i >= 0; i--){
            ans[i] *= suffix;
            suffix *= nums[i];
        }

        return ans;
    }
};
```
<!--IN this approach we are just using two variable pre and suff to store prefix and suffic -->
## Complexity
- **Time complexity:**O(n)
- **Space Complexity:**O(1);