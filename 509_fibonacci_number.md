# 509 Fibbonacci number

## Solution one for loop O(n)
```cpp
int fib(int n){
    if(n==0 || n==1) return n;
    vector<int> arr(n+1,0);
    arr[1]=1;
    for(int i=2;i<=n;i++){
        arr[i]=arr[i-1]+arr[1-2];

    }
    return arr[n];
}
```
### Complexity
- **Time:**O(n)
- **Space:**O(n)

## Solution two for loop improved space complexity

```cpp

int fib(int n){
    if(n<=1){
        return n;
    }
    int a=0;
    int b=1;
    int c;
    for(int i=2;i<=n;i++){
        c=a+b;
        a=b;
        b=c;

    }
    return c;
}
```
### complexity
- **Time:**O(n)
- **Space:**O(1)