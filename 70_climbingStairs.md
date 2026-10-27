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

## solution memoization

```cpp
class Solution {
public:
    int climb(int n,vector<int>& arr){
        if(n==1 || n==2) return n;
        if(arr[n]!=1) return arr[n];
        return arr[n]=climb(n-1,arr)+climb(n-2,arr);
    }
    int climbStairs(int n) {
        vector<int> arr(n+1,1);
        return climb(n,arr);
    }
};
```

## solution space optimization dp
```cpp
class Solution {
public:
    int climbStairs(int n) {
        int prev=0;
        int curr=1;
        int pre;
        for(int i=1;i<=n;i++){
            pre=prev+curr;
            prev=curr;
            curr=pre;

        }
        return pre;
    }
};
```
### Complexity 
**Time:** O(n)
**Space:** O(1)
