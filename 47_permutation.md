# 47 permutation

- All Similar to permutation 46 just we have to take care of duplicates
- And in one solution i have used sorting

## Solution sorting+ swap
```cpp
class Solution {
public:
    void f(int ind,int n,vector<int> nums,vector<vector<int>> &arr){
        if(ind==n){
            arr.push_back(nums);
            return;
        }
        for(int i=ind;i<n;i++){
            if(ind==i || nums[ind]!=nums[i]){
            swap(nums[ind],nums[i]);
            f(ind+1,n,nums,arr);
        }}
    }
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        sort(nums.begin(),nums.end());
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

## Solution using unordered_set + Swap
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

## solution 3 backtracking+ unordered set

```cpp
class Solution {
public:
    void f(int ind,int n,vector<int> &nums,vector<vector<int>> &arr){
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

# solution 4 boolean visited array + path +recursion
```cpp
class Solution {
public:
    void backtrack(vector<int>& nums, vector<bool>& visited, vector<int>& path, vector<vector<int>>& res) {
        if (path.size() == nums.size()) {
            res.push_back(path);
            return;
        }

        for (int i = 0; i < nums.size(); i++) {
            if (visited[i]) continue;

            
            if (i > 0 && nums[i] == nums[i - 1] && !visited[i - 1]) continue;

            visited[i] = true;
            path.push_back(nums[i]);
            
            backtrack(nums, visited, path, res);
            
            // Backtrack
            path.pop_back();
            visited[i] = false;
        }
    }

    vector<vector<int>> permuteUnique(vector<int>& nums) {
        sort(nums.begin(), nums.end()); // Crucial for this method to work
        vector<vector<int>> res;
        vector<int> path;
        vector<bool> visited(nums.size(), false);
        
        backtrack(nums, visited, path, res);
        return res;
    }
};

```

- **Time Complexity:**O(n*n!)
- **Space Complexity:**O(n*n!)