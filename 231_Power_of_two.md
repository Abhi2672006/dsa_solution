# 231 Power of two

## Solution one O(1) my first solution

```cpp
bool isPowerOfTwo(long int n){
    if(n<=0) return false;
    long int k=n-1;
    long int l=n&k;
    if(l) return true;
    return false;
}
```
### complexity
- **Time complexity:**O(1);
- **Space Complexity:**O(1);

## Solution 2 O(1) more optimized

```cpp
bool isPowerOfTwo(long int n){
    if(n<=0) return false;

    return (n & (n-1))==0;
}
```
### complexity
- **Time complexity:**O(1);
- **Space Complexity:**O(1);

## Solution 3 

```cpp
 bool isPowerOfTwo(long int n){
    if(n<=0) return false;
    if(n==1) return true;
    if(n%2!=0) return false;

    return isPowerOfTwo(n/2);
 }
 ```
 ### complexity
 - **Time Complexity:**O(logn) <!-- logn because we are dividing n by 2 at each step-->
 - **Space Complexity:**O(logn) <!-- log n because each recursive call adds a new to frame to the call stack in memory-->