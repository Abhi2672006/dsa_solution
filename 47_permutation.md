# 47 permutation

- All Similar to permutation 46 just we have to take care of duplicates
- And in one solution i have used sorting

## Solution sorting 
```cpp
class Solution {
public:
    void f(int ind,int n,vector<int> &nums,vector<vector<int>> &arr){
        if(ind==n){
            arr.push_back(nums);
            return;
        }
        for(int i=ind;i<n;i++){
            if(ind==i || nums[ind]!=nums[i]){
            swap(nums[ind],nums[i]);
            f(ind+1,n,nums,arr);
            swap(nums[i],nums[ind]);
        }}
    }
    vector<vector<int>> permute(vector<int>& nums) {
        sort(nums.begin(),nums.end()); //nlogn
        int n=nums.size();//O(1)
        vector<vector<int>> arr;
        f(0,n,nums,arr);
        return arr;
    }
};
```
### Complexity
- **Time Complexity:**O(n*n!)
- **Space Complexity:**O(n*n!)

## Solution using unordered_set
```cpp
class Solution {
public:
    void f(int ind,int n,vector<int> nums,vector<vector<int>> &arr){
        if(ind==n){
            arr.push_back(nums);
            return;
        }
        unordered_set<int> used;
        for(int i=ind;i<n;i++){
            if(used.find(nums[i])==used.end()){
            used.insert(nums[i]);
            swap(nums[ind],nums[i]);
            f(ind+1,n,nums,arr);
        }}
    }
    vector<vector<int>> permuteUnique(vector<int>& nums) {
       
        int n=nums.size();
        vector<vector<int>> arr;
        f(0,n,nums,arr);
        return arr;
    }
};
```


### Complexity
- **Time Complexity:**O(n*n!)
- **Space Complexity:**O(n*n!)

## solution 3 backtracking

```cpp
class Solution {
public:
    void f(int ind,int n,vector<int> nums,vector<vector<int>> &arr){
        if(ind==n){
            arr.push_back(nums);
            return;
        }
        unordered_set<int> used;
        for(int i=ind;i<n;i++){
            if(used.count(nums[i])) continue;
            used.insert(nums[i]);
            swap(nums[ind],nums[i]);
            f(ind+1,n,nums,arr);
            swap(nums[i],nums[ind]);

        }
    }
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        
        int n=nums.size();
        vector<vector<int>> arr;
        f(0,n,nums,arr);
        return arr;
    }
};
```

- **Time Complexity:**O(n*n!)
- **Space Complexity:**O(n*n!)
