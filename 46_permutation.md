# 46 Permutations

## Solution using map and recursion

```cpp
void f(int n,vector<vector<int>> &arr,vector<int> &arr1,vector<bool>&mp,int nums[]){
    if(arr1.size()==n){
        arr.push_back(arr1);
        return;
    }
    for(int i=0;i<n;i++){
        if(!mp[i]){
            mp[i]=true;
            arr1.push_back(nums[i]);
            f(n,arr,arr1,mp,nums);
            mp[i]=false;
            arr1.pop();
        }
    }

}
int main(){
    int nums[]={1,2,3};
    vector<vector<int>> arr;
    vector<int> arr1;
    vector<bool> mp(n,false);// u can also use unordered_map here
    
    int n=nums.size();
    f(n,arr,arr1,mp,nums);
    return arr;
}
```
### Complexity
- **Time Complexity:**O(n*n!)
- **Space Complexity:**O(n*n!)

## Solution 2 not using any external array

// this solution here works using call by value
```cpp
class Solution {
public:
    void f(int ind,int n,vector<int> nums,vector<vector<int>> &arr){
        if(ind==n){
            arr.push_back(nums);
            return;
        }
        for(int i=ind;i<n;i++){
            swap(nums[ind],nums[i]);
            f(ind+1,n,nums,arr);
        }
    }
    vector<vector<int>> permute(vector<int>& nums) {
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


## Solution 2 not using any external array call by reference

// this solution here works using call by reference
```cpp
class Solution {
public:
    void f(int ind,int n,vector<int> &nums,vector<vector<int>> &arr){
        if(ind==n){
            arr.push_back(nums);
            return;
        }
        for(int i=ind;i<n;i++){
            swap(nums[ind],nums[i]);
            f(ind+1,n,nums,arr);
            swap(nums[i],nums[ind]);

        }
    }
    vector<vector<int>> permute(vector<int>& nums) {
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
