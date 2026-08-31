# 90 Subsets 2

## solution Backtrack

```cpp

void getall(int ind,int n,vector<vector<int>> &arr,vector<int> &arr1,vector<int> nums){
    if(ind==n){
        arr.push_back(arr1);
        return;
    }

    arr1.push_back(nums[ind]);
    getall(ind+1,n,arr,arr1,nums);
    arr.pop();
    int next=ind+1;
    while(next<n && nums[ind]==nums[next]) next++;
    getall(next,n,arr,arr1,nums);
}
int main(){
    int nums[]={1,2,2};
    int n=nums.size();
    vector<vector<int>> arr;
    vector<int> arr1;
    int ind=0;
    getall(ind,n,arr,arr1,nums);
     return arr;

}
```
### Complexity
- **Time Complexity:**O(n*2^n) 
- **Space Complexity:**O(n*2^n)


