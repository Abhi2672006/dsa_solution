# 70 Climbling Stairs

## solution dp
```cpp
int climb(vector<int> &arr,int n){
    if(n<=2) return n;

    if(arr[n]!=-1) return arr[n];
    return arr[n]=climb(arr,n-1)+climb(arr,n-2);
}
int climbstairs(int n){
    vector<int> arr(n+1,-1);

    return climb(arr,n);

}
```
### complexity
- **Time Complexity:**O(n)
- **Space Complexity:**O(n)