# 78 Subset

## Solution using Backtracking using recursion with an include/exclude choice.

```cpp
class Solution {
public:
    void f(int ind,int &n,vector<vector<int>> &arr,vector<int> &nums,vector<int> &arr1){
        if(ind==n){
            arr.push_back(arr1);
            return;
        }
        arr1.push_back(nums[ind]);
        f(ind+1,n,arr,nums,arr1);
        arr1.pop_back();
        f(ind+1,n,arr,nums,arr1);
    }
    vector<vector<int>> subsets(vector<int>& nums) {
        int n=nums.size();
        vector<vector<int>> arr1;
        vector<int> arr;
        f(0,n,arr1,nums,arr);
        return arr1;
    }
};
```
### Complexity
- **Time Complexity:**O(n*2^n)
- **Space Complexity:**O(n*2^n)

### Explanation

At every index, we have two choices:
1. Include the current element.
2. Exclude the current element.

Time complexity is O(n*2^n) because for every elements there are two choices then if there are three elements there can be upto 8 subset can be possible and each set can go upto total number of elements in the array so it can go upto n
Space complexity if O(n*2^n) for output the subset can contain at most upto 2^n elements and each subset store upto n elements so same as time complexity
and O(n) is auxiliary space for recursion stack